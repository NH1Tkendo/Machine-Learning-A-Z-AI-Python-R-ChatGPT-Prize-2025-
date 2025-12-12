## Ghi chú Bài học: Xử lý Dữ liệu cho Hồi quy Tuyến tính Đa biến (Multiple Linear Regression)

## Nhập thư viện và Tập dữ liệu (Import Libraries & Dataset)

- Bước đầu tiên là nhập các thư viện cần thiết và tải tập dữ liệu lên môi trường làm việc (notebook).
    
- Sau khi nhập dữ liệu, chúng ta có:
    
    - **Ma trận các đặc trưng (Matrix of features - X)**: Chứa các biến độc lập.
        
    - **Vectơ biến phụ thuộc (Dependent variable vector - y)**: Chứa biến mục tiêu cần dự đoán.
        

## Kiểm tra và Mã hóa dữ liệu (Data Inspection & Encoding)

- **Trước khi mã hóa (Before Encoding)**:
    
    - Khi in ma trận $X$, thứ tự các cột tương ứng với tập dữ liệu gốc: `R&D Spend`, `Administration Spend`, `Marketing Spend`, và `State`.
        
    - Cột `State` chứa dữ liệu dạng chữ (categorical data).
        
- **Mã hóa dữ liệu phân loại (Encoding Categorical Data)**:
    
    - Sử dụng phương pháp **Mã hóa One-Hot (One-Hot Encoding)** để chuyển đổi cột `State`.
        
    - **Kết quả sau khi mã hóa**:
        
        - Các cột biến giả (dummy variables) mới được tạo ra sẽ nằm ở **đầu** ma trận $X$.
            
        - Các cột ban đầu (`R&D Spend`, `Administration Spend`, `Marketing Spend`) sẽ bị đẩy về sau.
            
    - **Ví dụ minh họa từ tập dữ liệu**:
        
        - `New York` $\rightarrow$ Mã hóa thành `0.0, 0.0, 1.0`
            
        - `California` $\rightarrow$ Mã hóa thành `1.0, 0.0, 0.0`
            
        - `Florida` $\rightarrow$ Mã hóa thành `0.0, 1.0, 0.0`
            

## Lưu ý về Quy mô đặc trưng (Feature Scaling)

- **Không cần áp dụng Quy mô đặc trưng (Feature Scaling)** trong Hồi quy Tuyến tính Đa biến.
    
- **Lý do**:
    
    - Trong phương trình hồi quy: $y = b_0 + b_1x_1 + b_2x_2 + ... + b_nx_n$
        
    - Mỗi biến độc lập ($x$) được nhân với một hệ số ($b$).
        
    - Các hệ số này sẽ tự điều chỉnh (compensate) để đưa tất cả các biến về cùng một quy mô, bất kể giá trị ban đầu của đặc trưng lớn hay nhỏ.
        

## Các giả định của Hồi quy Tuyến tính (Linear Regression Assumptions)

- **Quan điểm thực hành**: Không bắt buộc phải kiểm tra các giả định của hồi quy tuyến tính trước khi xây dựng mô hình.
    
- **Lý do**:
    
    - Nếu dữ liệu có mối quan hệ tuyến tính: Mô hình sẽ hoạt động tốt và cho độ chính xác cao.
        
    - Nếu dữ liệu _không_ có mối quan hệ tuyến tính: Mô hình sẽ hoạt động kém (độ chính xác thấp).
        
- **Quy trình làm việc hiệu quả**:
    
    1. Thử nghiệm nhiều mô hình khác nhau trên tập dữ liệu.
        
    2. So sánh độ chính xác.
        
    3. Nếu Hồi quy Tuyến tính Đa biến có độ chính xác thấp hơn các mô hình khác, ta chỉ cần loại bỏ nó và chọn mô hình tốt hơn.
        
    4. Việc kiểm tra thủ công các giả định được coi là lãng phí thời gian trong quy trình lựa chọn mô hình thực tế.
        

## Bước tiếp theo

- Sau khi tiền xử lý dữ liệu (Data Pre-processing) hoàn tất, bước kế tiếp là **huấn luyện mô hình (Training the model)** trên tập huấn luyện.