## Thiết lập và Chuẩn bị dữ liệu cho Decision Tree Regression

## 1. Tải và nhập dữ liệu trên Google Colab

Quy trình chuẩn bị môi trường làm việc bao gồm:

1. Nhấp vào biểu tượng thư mục (Folder) để kết nối với môi trường chạy (runtime).
    
2. Tải lên tập dữ liệu `Position_Salaries.csv` từ thư mục `Part 2 Regression/Decision Tree Regression/Python`.
    
3. Chạy 2 ô mã (code cells) đầu tiên để:
    
    - Nhập các thư viện cần thiết (Importing libraries).
        
    - Nhập tập dữ liệu (Importing the dataset) để tạo ma trận đặc trưng $X$ và vectơ biến phụ thuộc $y$.
        

## 2. Hướng dẫn tùy chỉnh cho các tập dữ liệu khác

Mã nguồn này có thể tái sử dụng cho các bài toán khác với một số điều chỉnh cần thiết:

- **Tên tập dữ liệu**: Thay đổi đường dẫn/tên file `csv` tương ứng.
    
- **Lựa chọn cột cho ma trận $X$**:
    
    - Trong bài này, cột đầu tiên bị loại bỏ vì nội dung trùng lặp với cột mức độ (level).
        
    - Với dữ liệu mới, hãy kiểm tra kỹ để quyết định có giữ lại tất cả các cột hay không.
        
- **Xử lý dữ liệu (Data Pre-processing)**:
    
    - Kiểm tra và xử lý dữ liệu bị thiếu (Missing data).
        
    - Mã hóa dữ liệu phân loại (Categorical data):
        
        - Nếu thứ tự quan trọng (ví dụ: kích cỡ quần áo): Dùng **Label Encoder**.
            
        - Nếu thứ tự không quan trọng (ví dụ: quốc gia, tên bang): Dùng **Column Transformer** với **One-Hot Encoder**.
            

## 3. Quy tắc về Feature Scaling (Mở rộng tính năng)

Một đặc điểm quan trọng của mô hình Cây quyết định (Decision Tree) và Rừng ngẫu nhiên (Random Forest):

- **Không cần áp dụng Feature Scaling**.
    
- **Lý do**:
    
    - Các dự đoán của mô hình này là kết quả của việc phân chia dữ liệu liên tiếp (successive splits) thông qua các nút của cây.
        
    - Mô hình không dựa trên các phương trình toán học đại số như Hồi quy tuyến tính hay SVR, do đó sự khác biệt về độ lớn giá trị giữa các biến không ảnh hưởng đến việc phân loại/phân nhánh.
        
- **Lưu ý**: Bạn vẫn có thể chia tập dữ liệu thành _Training set_ và _Test set_ nếu cần đánh giá mô hình, nhưng bước Scaling là không bắt buộc.
    

## 4. Chiến lược huấn luyện hiện tại

Trong bài thực hành này, chúng ta sẽ thực hiện:

- **Huấn luyện trên toàn bộ tập dữ liệu**: Không chia tách dữ liệu để tận dụng tối đa lượng thông tin từ tập dữ liệu nhỏ.
    
- **Mục tiêu**:
    
    1. Xây dựng mô hình Decision Tree Regression.
        
    2. Dự đoán mức lương cho vị trí cấp độ 6.5.
        
    3. Trực quan hóa đường hồi quy (Regression curve).