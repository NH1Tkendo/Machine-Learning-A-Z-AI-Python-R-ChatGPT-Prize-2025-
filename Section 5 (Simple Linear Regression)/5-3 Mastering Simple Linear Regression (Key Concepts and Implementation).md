## Tổng quan về Hồi quy (Regression)

## Khái niệm

- Hồi quy là một nhánh của học máy (Machine Learning) nhằm mục đích dự đoán các **số thực liên tục (continuous real numbers)**.
    
- Ví dụ: Dự đoán mức lương, nhiệt độ, hoặc bất kỳ giá trị số nào.
    

## Lộ trình học tập các mô hình Hồi quy

Khóa học sẽ cung cấp một bộ công cụ ("toolkit") gồm các mô hình khác nhau để xử lý dữ liệu:

1. **Hồi quy tuyến tính đơn giản (Simple Linear Regression)**: Mô hình đơn giản nhất, chỉ có một biến độc lập (feature).
    
2. **Hồi quy tuyến tính đa biến (Multiple Linear Regression)**: Sử dụng nhiều biến độc lập (features) để dự đoán.
    
3. **Hồi quy đa thức (Polynomial Regression)**: Xử lý các tập dữ liệu phi tuyến tính (non-linear correlations).
    
4. **Hồi quy hỗ trợ vector (Support Vector Regression - SVR)**: Một mô hình phi tuyến tính khác.
    
5. **Hồi quy cây quyết định (Decision Tree Regression) & Rừng ngẫu nhiên (Random Forest Regression)**: Các giải pháp thay thế để xử lý dữ liệu phi tuyến tính.
    

**Chiến lược áp dụng**: Khi gặp bài toán thực tế, bạn có thể thử tất cả các mô hình trong bộ công cụ này và chọn mô hình có độ chính xác cao nhất.

---

## Dự án thực hành: Hồi quy tuyến tính đơn giản với Python

## Mục tiêu

Xây dựng mô hình đầu tiên để hiểu rõ quy trình trước khi chuyển sang các dữ liệu phức tạp hơn. Chúng ta sẽ sử dụng các mẫu mã nguồn (code templates) tổng quát để dễ dàng tái sử dụng cho các dữ liệu khác sau này.

## Phân tích bộ dữ liệu (Dataset)

- **Tên file**: `Salary_Data.csv`
    
- **Quy mô**: Dữ liệu đơn giản gồm 30 quan sát (observations) để tập trung vào việc học cách xây dựng mô hình.
    
- **Cấu trúc dữ liệu**:
    
    - Mỗi hàng tương ứng với một nhân viên cụ thể trong công ty.
        
    - Cột 1 - **Biến độc lập/Đặc trưng (Feature)**: Số năm kinh nghiệm (`YearsExperience`).
        
    - Cột 2 - **Biến phụ thuộc (Dependent Variable)**: Mức lương (`Salary`).
        

## Bài toán cần giải quyết

- **Nhiệm vụ**: Xây dựng mô hình hồi quy tuyến tính đơn giản để tìm ra mối tương quan (correlation) giữa **số năm kinh nghiệm** và **mức lương**.
    
- **Ứng dụng**: Dự đoán mức lương phù hợp cho một nhân viên mới dựa trên số năm kinh nghiệm của họ.