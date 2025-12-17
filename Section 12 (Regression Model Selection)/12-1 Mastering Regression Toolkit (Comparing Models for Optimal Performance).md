## Đánh giá & Lựa chọn Mô hình Hồi quy

Phần này hướng dẫn cách đánh giá các mô hình hồi quy và lựa chọn mô hình tốt nhất cho một bộ dữ liệu cụ thể.

## Vấn đề và Giải pháp

- **Câu hỏi**: Với nhiều mô hình hồi quy đã học (hồi quy tuyến tính, đa thức, SVR, cây quyết định, rừng ngẫu nhiên), làm thế nào để chọn ra mô hình phù hợp nhất cho bộ dữ liệu của mình?
    
- **Giải pháp**: Cách tiếp cận đơn giản và hiệu quả nhất là **thử nghiệm tất cả các mô hình** trên cùng một bộ dữ liệu, sau đó so sánh hiệu suất của chúng và chọn ra mô hình có kết quả tốt nhất.
    

## Chỉ số đánh giá hiệu suất

- Hiệu suất của mô hình hồi quy thường được đo bằng hệ số xác định `R-bình phương (R-squared)` hoặc `R-bình phương điều chỉnh (Adjusted R-squared)`.
    
- Mô hình có chỉ số này cao hơn được xem là tốt hơn.
    

## Giới thiệu Bộ công cụ Hồi quy (Regression Toolkit)

- Đây là một tập hợp các mẫu mã nguồn (code template) được xây dựng sẵn cho các mô hình hồi quy đã học.
    
- Các mẫu này được thiết kế để có thể tái sử dụng một cách linh hoạt, chỉ cần thay đổi một vài thông tin nhỏ (như tên file dữ liệu) là có thể áp dụng ngay cho các bộ dữ liệu mới.
    
- Mỗi mẫu mã nguồn đều tích hợp sẵn công cụ đánh giá, giúp so sánh hiệu suất giữa các mô hình một cách nhanh chóng và hiệu quả.
    

## Cấu trúc Thư mục

- Bộ công cụ này nằm trong một thư mục mới có tên là **Model Selection**, tách biệt với thư mục chính của khóa học.
    
- Thư mục này được dùng chuyên cho việc triển khai và lựa chọn mô hình tốt nhất (bao gồm cả hồi quy và phân loại).
    
- Bên trong `Model Selection`, có thư mục con `Regression` chứa các mô hình hồi quy.
    

## Các mô hình trong bộ công cụ

Thư mục `Regression` chứa 5 loại mô hình hồi quy, phù hợp cho các bộ dữ liệu có nhiều biến độc lập (features):

- Hồi quy tuyến tính bội (Multiple Linear Regression)
    
- Hồi quy đa thức (Polynomial Regression)
    
- Hồi quy vector hỗ trợ (Support Vector Regression - SVR)
    
- Hồi quy cây quyết định (Decision Tree Regression)
    
- Hồi quy rừng ngẫu nhiên (Random Forest Regression)
    

## Điều kiện để sử dụng mẫu

Để các mẫu mã nguồn hoạt động chính xác, bộ dữ liệu của bạn cần đáp ứng các điều kiện sau:

- **Định dạng file**: `CSV`.
    
- **Cấu trúc dữ liệu**:
    
    - Các cột đầu tiên chứa các biến độc lập (features).
        
    - Cột cuối cùng chứa biến phụ thuộc (dependent variable).
        
- **Xử lý dữ liệu**: Bộ dữ liệu ví dụ được sử dụng trong phần này đã được làm sạch:
    
    - Không có dữ liệu bị thiếu (missing values).
        
    - Không có dữ liệu dạng chuỗi (categorical data).
        
    - Người học được kỳ vọng sẽ tự áp dụng các kỹ thuật tiền xử lý dữ liệu đã học trước đó nếu cần.