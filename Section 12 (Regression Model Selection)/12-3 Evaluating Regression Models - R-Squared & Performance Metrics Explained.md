## Cấu trúc Code Templates cho các Mô hình Hồi quy

Giảng viên giới thiệu cấu trúc mã nguồn cho 4 mô hình còn lại (sau Hồi quy tuyến tính bội). Điểm chung quan trọng nhất là tính **tổng quát hóa (generic)**: bạn chỉ cần thay đổi tên bộ dữ liệu là có thể chạy được mô hình.

## 1. Hồi quy Đa thức (Polynomial Regression)

- **Tiền xử lý dữ liệu**:
    
    - Nhập thư viện và dữ liệu (chỉ cần thay tên file dataset).
        
    - Chia tập dữ liệu thành Training set và Test set.
        
- **Huấn luyện**:
    
    - Sử dụng mã nguồn đã học ở phần trước (với bậc `degree = 4`).
        
    - Huấn luyện mô hình trên tập Training set.
        
- **Dự đoán & Đánh giá**:
    
    - Dự đoán kết quả trên tập Test set để so sánh với giá trị thực tế.
        
    - Đánh giá hiệu suất mô hình (sẽ được đề cập chi tiết ở phần sau).
        

## 2. Hồi quy Vector Hỗ trợ (Support Vector Regression - SVR)

Đây là mô hình yêu cầu xử lý dữ liệu kỹ hơn do đặc thù của thuật toán.

- **Tiền xử lý đặc biệt**:
    
    - **Reshape (Định hình lại)**: Phải thay đổi kích thước vector biến phụ thuộc ($y$) trước khi feature scaling.
        
    - **Feature Scaling (Quy mô hóa đặc trưng)**: Bắt buộc đối với SVR.
        
        - Cần 2 bộ `Scalers` riêng biệt: một cho ma trận đặc trưng ($X$) và một cho vector biến phụ thuộc ($y$).
            
- **Quy trình**:
    
    - Nhập dữ liệu $\rightarrow$ Reshape $y$ $\rightarrow$ Chia Training/Test set $\rightarrow$ Feature Scaling.
        
    - Huấn luyện SVR trên Training set.
        
    - Dự đoán trên Test set và đánh giá hiệu suất bằng $R^2$.
        

## 3. Hồi quy Cây quyết định (Decision Tree Regression)

- **Đặc điểm**: Không yêu cầu Feature Scaling.
    
- **Quy trình**:
    
    - Nhập thư viện và dữ liệu (thay tên dataset).
        
    - Chia tập dữ liệu thành Training set và Test set.
        
    - Huấn luyện mô hình trên Training set (code giống hệt bài học trước).
        
    - Dự đoán kết quả trên Test set để có cái nhìn ban đầu về hiệu suất.
        
    - Đánh giá mô hình bằng $R^2$.
        

## 4. Hồi quy Rừng ngẫu nhiên (Random Forest Regression)

- **Quy trình**: Tương tự như Cây quyết định.
    
    - Tiền xử lý dữ liệu cơ bản (không cần scaling).
        
    - Nhập tên dataset.
        
    - Huấn luyện mô hình Random Forest trên Training set.
        
    - Dự đoán kết quả trên Test set.
        
    - Đánh giá cuối cùng bằng $R^2$.
        

---

## Đánh giá Hiệu suất Mô hình (Model Evaluation)

Phần quan trọng nhất để chọn ra mô hình tốt nhất là bước đánh giá cuối cùng trong mỗi file code.

- **Chỉ số sử dụng**: Hệ số $R^2$ (R-squared coefficient).
    
- **Phương pháp học tập**:
    
    - Giảng viên khuyến khích tư duy độc lập (independent learning).
        
    - Thay vì đưa ngay đoạn code, bài học sẽ mô phỏng quá trình tìm kiếm giải pháp trên tài liệu trực tuyến (documentation) để người học biết cách tự tra cứu khi gặp vấn đề mới.
        

> **Ghi chú**: Tất cả các mẫu code này đều tuân thủ nguyên tắc:
> 
> 1. Dữ liệu đầu vào sạch (không missing, không categorical).
>     
> 2. Cột cuối cùng là biến phụ thuộc.
>     
> 3. Chỉ cần thay đổi đường dẫn/tên file dữ liệu là có thể chạy ("Plug and Play").
>