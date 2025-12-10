## Chuẩn hóa tập kiểm tra và Hoàn thiện Template

## Quy trình chuẩn hóa tập kiểm tra (Test Set)

Sau khi đã huấn luyện `StandardScaler` trên tập huấn luyện (`X_train`), bước tiếp theo là áp dụng phép biến đổi tương tự lên tập kiểm tra (`X_test`).

**Nguyên tắc quan trọng:**

- **Không dùng `fit` hoặc `fit_transform` trên `X_test`**: Việc này sẽ tính toán lại trung bình và độ lệch chuẩn mới dựa trên dữ liệu kiểm tra, làm sai lệch mô hình.
    
- **Chỉ dùng phương thức `transform`**: Phải sử dụng lại chính bộ scaler (với mean và std đã học từ `X_train`) để biến đổi `X_test`.
    
- Điều này đảm bảo tính nhất quán: dữ liệu kiểm tra được xử lý giống hệt như dữ liệu huấn luyện, giúp mô hình đưa ra dự đoán chính xác.
    

**Mã nguồn thực hiện:**

python

`# Chỉ áp dụng transform cho X_test X_test[:, 3:] = sc.transform(X_test[:, 3:])`

## Kết quả sau khi chuẩn hóa

- **Biến giả (Dummy Variables)**: Giữ nguyên giá trị 0 và 1 (nằm trong khoảng an toàn [-3, +3]).
    
- **Biến số thực (Age, Salary)**: Được chuyển đổi về thang đo mới, thường nằm trong khoảng [-2, +2] hoặc [-3, +3].
    
- **Lợi ích**: Tất cả các biến giờ đây có cùng một quy mô, giúp tối ưu hóa quá trình huấn luyện cho một số mô hình máy học cụ thể.
    

## Mẫu xử lý dữ liệu (Data Pre-processing Template)

Để tăng tốc độ làm việc cho các bài toán sau này, giảng viên giới thiệu một mẫu code chuẩn (template) bao gồm các bước luôn luôn phải thực hiện.

**Cấu trúc Template:**

1. **Nhập thư viện (Importing Libraries)**: Luôn cần thiết.
    
2. **Nhập dữ liệu (Importing Dataset)**:
    
    - Code được viết tổng quát để tự động lấy tất cả cột trừ cột cuối làm features (X) và cột cuối cùng làm biến phụ thuộc (y).
        
    - **Điểm duy nhất cần thay đổi**: Tên file dữ liệu (`dataset.csv`).
        
3. **Chia tách dữ liệu (Splitting Dataset)**: Tách thành Training set và Test set. Phần này thường không cần chỉnh sửa gì.
    

> **Lưu ý**: Bước Feature Scaling (Chuẩn hóa) không được đưa vào template mặc định vì không phải mô hình nào cũng cần đến nó.

## Tổng kết phần Tiền xử lý dữ liệu

- Chúng ta đã hoàn thành bộ công cụ tiền xử lý dữ liệu (Data Pre-processing Toolkit).
    
- Các kỹ thuật đã học: Xử lý dữ liệu thiếu, Mã hóa dữ liệu phân loại, Chia tách tập dữ liệu, và Chuẩn hóa đặc trưng.
    
- Bước tiếp theo: Bắt đầu xây dựng các mô hình máy học thực tế, khởi đầu với các mô hình **Hồi quy (Regression)**.