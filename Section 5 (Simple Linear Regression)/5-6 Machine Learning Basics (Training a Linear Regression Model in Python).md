## Phương thức huấn luyện `fit`

## Tầm quan trọng

Phương thức `fit` là công cụ cơ bản và quan trọng nhất để huấn luyện các mô hình học máy, từ các mô hình hồi quy đơn giản đến mạng nơ-ron phức tạp trong trí tuệ nhân tạo.

## Cú pháp và cách sử dụng

- **Gọi phương thức**: `regressor.fit()`
    
- **Đối tượng**: `regressor` (đối tượng của lớp `LinearRegression` đã tạo trước đó).
    
- **Tham số đầu vào**: Phương thức `fit` yêu cầu 2 tham số chính theo đúng thứ tự:
    
    1. `X_train`: Ma trận các biến độc lập (features) của tập huấn luyện.
        
    2. `y_train`: Vectơ biến phụ thuộc (dependent variable) của tập huấn luyện.
        

**Mã nguồn thực hiện:**

python

`regressor.fit(X_train, y_train)`

## Ý nghĩa hoạt động

- Phương thức này sẽ "dạy" mô hình tìm ra mối liên hệ (hồi quy) giữa các đặc trưng (`X_train`) và kết quả mục tiêu (`y_train`).
    
- Khi chạy lệnh này, nếu thành công, output sẽ trả về thông tin xác nhận mô hình `LinearRegression` đã được tạo với các tham số mặc định.
    

---

## Bài tập thực hành tiếp theo: Dự đoán kết quả

Sau khi đã huấn luyện xong mô hình trên tập huấn luyện (`X_train`, `y_train`), bước tiếp theo là kiểm tra khả năng dự đoán của nó trên tập kiểm tra (`test set`).

## Yêu cầu

- Sử dụng mô hình đã huấn luyện để dự đoán kết quả cho các dữ liệu mới.
    
- **Gợi ý**: Sử dụng phương thức có tên là `predict`.
    

## Hướng dẫn tự thực hiện

1. Tìm hiểu cách sử dụng phương thức `predict` của thư viện Scikit-learn.
    
2. Áp dụng phương thức này lên tập dữ liệu kiểm tra (`X_test`) để tạo ra các dự đoán.
    
3. Kết quả sẽ được so sánh với kết quả thực tế (`y_test`) ở các bước sau.