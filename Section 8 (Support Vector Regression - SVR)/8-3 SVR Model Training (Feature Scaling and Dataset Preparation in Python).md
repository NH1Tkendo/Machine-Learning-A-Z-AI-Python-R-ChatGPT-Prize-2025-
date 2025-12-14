## Thực hành: Support Vector Regression (SVR)

## Tổng quan và Mục tiêu

- Đây là bài thực hành nâng cao hơn so với các mô hình trước đây.
    
- **Mục tiêu chính**: Không chỉ xây dựng mô hình SVR mà còn phải thành thạo kỹ thuật **Quy chuẩn hóa dữ liệu (Feature Scaling)**.
    
- Người học sẽ biết cách áp dụng quy chuẩn hóa và quan trọng hơn là **nghịch đảo quy chuẩn (inverse transformation)** để đưa dữ liệu về thang đo gốc.
    

## Bộ dữ liệu và Bài toán

- **Dữ liệu**: Sử dụng lại bộ dữ liệu "Position Salaries" (Mức lương theo vị trí).
    
    - Đặc trưng ($X$): Cấp độ vị trí (Position Level) từ 1 đến 10.
        
    - Mục tiêu ($Y$): Lương (Salary) từ 45.000 đến 1.000.000 USD.
        
    - Mối quan hệ giữa $X$ và $Y$ là phi tuyến tính (non-linear).
        
- **Kịch bản**:
    
    - Tuyển dụng một nhân sự mới ở cấp độ 6.5 (Regional Manager).
        
    - Ứng viên mong muốn mức lương 160k USD dựa trên công ty cũ.
        
    - **Nhiệm vụ**: Huấn luyện SVR để dự đoán mức lương chuẩn cho cấp độ 6.5 và so sánh với kết quả của Hồi quy đa thức (Polynomial Regression).
        

## Tại sao cần Feature Scaling cho SVR?

Đây là điểm khác biệt quan trọng so với các mô hình Hồi quy tuyến tính (Linear Regression).

1. **Đối với Hồi quy tuyến tính (Simple, Multiple, Polynomial)**:
    
    - Không bắt buộc phải quy chuẩn hóa dữ liệu.
        
    - Lý do: Phương trình có các hệ số (coefficients) đi kèm với mỗi đặc trưng. Các hệ số này có thể tự điều chỉnh (ví dụ: trở nên rất nhỏ) để bù đắp cho các đặc trưng có giá trị lớn.
        
2. **Đối với Support Vector Regression (SVR)**:
    
    - **Bắt buộc phải áp dụng Feature Scaling**.
        
    - Lý do: SVR có một phương trình ẩn (implicit equation) biểu diễn mối quan hệ giữa $Y$ và $X$. Nó không có các hệ số tường minh để bù đắp sự chênh lệch về độ lớn giữa các đặc trưng.
        
    - Nếu không quy chuẩn, mô hình sẽ hoạt động kém hiệu quả do sự chênh lệch thang đo.
        

## Cấu trúc bài thực hành (Implementation Steps)

Quy trình thực hiện trong Python sẽ bao gồm các bước sau:

1. **Nhập thư viện (Import Libraries)**.
    
2. **Nhập dữ liệu (Import Dataset)**.
    
3. **Áp dụng Feature Scaling**: Bước quan trọng nhất trong bài này.
    
4. **Huấn luyện mô hình (Training)**:
    
    - Huấn luyện SVR trên **toàn bộ bộ dữ liệu**.
        
    - Không chia tách tập Train/Test để tận dụng tối đa lượng dữ liệu nhỏ nhằm học các tương quan.
        
5. **Dự đoán kết quả (Prediction)**:
    
    - Dự đoán lương cho cấp độ 6.5.
        
    - Cần sử dụng kỹ thuật nghịch đảo quy chuẩn để ra con số lương thực tế (USD).
        
6. **Trực quan hóa (Visualization)**:
    
    - Vẽ biểu đồ kết quả SVR ở độ phân giải thấp và cao.
        
    - So sánh đường cong hồi quy với dữ liệu thực tế.