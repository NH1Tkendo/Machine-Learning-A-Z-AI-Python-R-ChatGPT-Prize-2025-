## Dự đoán và Hiển thị Kết quả trên Tập kiểm tra

## Tạo vectơ dự đoán

Bước đầu tiên là sử dụng mô hình đã huấn luyện để dự đoán lợi nhuận dựa trên các đặc trưng của tập kiểm tra.

- **Biến lưu trữ**: `y_pred` (chứa các giá trị lợi nhuận được dự đoán).
    
- **Phương thức**: `regressor.predict(X_test)`
    
    - Đầu vào `X_test`: Chứa các biến độc lập của tập kiểm tra (đã bao gồm các biến giả One-Hot Encoding và các cột chi phí).
        

python

`# Dự đoán lợi nhuận trên tập kiểm tra y_pred = regressor.predict(X_test)`

## Định dạng hiển thị số liệu

Để kết quả dễ đọc hơn, ta thiết lập cấu hình in số thực với độ chính xác 2 chữ số thập phân.

python

`import numpy as np # Thiết lập độ chính xác khi in số thực là 2 chữ số thập phân np.set_printoptions(precision=2)`

## Hiển thị so sánh: Lợi nhuận Dự đoán vs Lợi nhuận Thực tế

Để so sánh trực quan, ta sẽ ghép hai vectơ `y_pred` (dự đoán) và `y_test` (thực tế) lại với nhau theo chiều dọc.

## Kỹ thuật Reshape (Thay đổi hình dạng)

Vectơ trong NumPy mặc định thường được hiển thị theo chiều ngang (1 hàng). Để ghép chúng theo chiều dọc (cột bên trái là dự đoán, cột bên phải là thực tế), ta cần chuyển đổi chúng thành dạng cột đứng.

- **Hàm sử dụng**: `.reshape(len(y_pred), 1)`
    
    - Tham số 1: Số lượng hàng (bằng độ dài của vectơ).
        
    - Tham số 2: Số lượng cột (là 1).
        

## Kỹ thuật Concatenate (Nối mảng)

Sử dụng hàm `np.concatenate` để nối hai vectơ đã được reshape.

- **Cấu trúc hàm**: `np.concatenate((a1, a2), axis=1)`
    
    - `(a1, a2)`: Tuple chứa các mảng cần nối.
        
    - `axis=1`: Nối theo chiều ngang (đặt hai cột cạnh nhau). Nếu muốn nối dọc (chồng lên nhau) thì dùng `axis=0` (mặc định), nhưng ở đây ta muốn so sánh từng cặp giá trị nên sẽ đặt chúng cạnh nhau.
        

**Lưu ý**: Trong đoạn transcript, giảng viên dùng từ "concatenate vertically" (nối dọc) nhưng mô tả kỹ thuật `reshape` thành cột và đặt cạnh nhau, thực chất là tạo ra một ma trận 2 cột để so sánh từng hàng.

python

`# In ra kết quả so sánh: Cột trái là Dự đoán, Cột phải là Thực tế print(np.concatenate((y_pred.reshape(len(y_pred),1), y_test.reshape(len(y_test),1)),1))`

## Ý nghĩa của việc so sánh

- Việc hiển thị hai cột số liệu cạnh nhau giúp ta đánh giá nhanh hiệu suất của mô hình bằng mắt thường.
    
- Ta có thể thấy ngay sự chênh lệch giữa lợi nhuận dự đoán và lợi nhuận thực tế cho từng startup trong tập kiểm tra.