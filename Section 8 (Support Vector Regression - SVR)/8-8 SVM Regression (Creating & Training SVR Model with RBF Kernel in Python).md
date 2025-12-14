## Xây dựng và Huấn luyện Mô hình SVR

## 1. Import Thư viện và Class

Mô hình SVR nằm trong module `svm` của thư viện Scikit-Learn.

python

`from sklearn.svm import SVR`

## 2. Khởi tạo Mô hình (SVR Instance)

![[VSM-Kernel.png]]
Khi khởi tạo đối tượng SVR, tham số quan trọng nhất cần xác định là `kernel` (hàm nhân).

- **Linear Kernel**: Dùng cho các mối quan hệ tuyến tính.
    
- **Non-linear Kernels**: Dùng cho dữ liệu phức tạp, phi tuyến tính. Các loại phổ biến:
    
    - Polynomial Kernel
        
    - Gaussian Kernel
        
    - Sigmoid Kernel
        
    - **Radial Basis Function (RBF) Kernel**: Đây là kernel phổ biến và hiệu quả nhất, thường được khuyến nghị sử dụng khi bắt đầu thử nghiệm.
        

**Mã nguồn khởi tạo:**

python

`# Khởi tạo SVR với RBF Kernel regressor = SVR(kernel='rbf')`

## 3. Huấn luyện Mô hình (Training)

Do không chia tách dữ liệu, ta huấn luyện mô hình trên toàn bộ bộ dữ liệu đã được **Feature Scaling** ở bước trước.

- Sử dụng phương thức `.fit(X, y)`.
    
- **Đầu vào**:
    
    - `X`: Ma trận đặc trưng đã quy chuẩn (scaled features).
        
    - `y`: Vector biến phụ thuộc đã quy chuẩn (scaled target).
        

**Mã nguồn huấn luyện:**

python

`regressor.fit(X, y)`

_Lưu ý: Nếu `y` ở dạng vector cột 2 chiều (do bước reshape trước đó), có thể cần dùng `.ravel()` hoặc `.flatten()` nếu gặp cảnh báo về DataConversionWarning, tùy phiên bản Scikit-Learn._

## 4. Vấn đề cần giải quyết tiếp theo

Sau khi huấn luyện, mô hình sẽ đưa ra dự đoán dựa trên thang đo đã quy chuẩn (scaled values).

- Kết quả dự đoán sẽ nằm trong khoảng nhỏ (ví dụ: -1 đến 3), **không phải** là mức lương thực tế (USD).
    
- **Bước tiếp theo bắt buộc**: Phải thực hiện **nghịch đảo quy chuẩn (Inverse Scaling)** để chuyển đổi kết quả dự đoán về thang đo gốc ban đầu.