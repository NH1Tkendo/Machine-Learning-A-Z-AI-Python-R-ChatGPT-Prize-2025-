## Thực nghiệm Chọn lựa Mô hình (Model Selection Demo)

## 1. Yêu cầu và Chuẩn bị dữ liệu

Code mẫu (code templates) được thiết kế để hoạt động với bất kỳ bộ dữ liệu nào, miễn là đáp ứng các điều kiện sau:

- **Cấu trúc dữ liệu**: Các cột đặc trưng `(features)` nằm ở đầu và cột biến phụ thuộc `(dependent variable)` nằm ở cuối cùng.
    
- **Tiền xử lý**: Dữ liệu đã được xử lý các giá trị thiếu `(missing data)` và mã hóa dữ liệu định danh `(categorical data)`.
    

**Bộ dữ liệu sử dụng trong demo (`data.csv`)**:

- **Đầu vào (Features)**: Nhiệt độ môi trường `(ambient temperature)`, Độ chân không `(vacuum)`, Áp suất môi trường `(ambient pressure)`, Độ ẩm `(humidity)`.
    
- **Mục tiêu (Target)**: Dự đoán sản lượng năng lượng `(energy output)`.
    

## 2. Quy trình Thực hiện trên Google Colab

Để so sánh hiệu quả giữa các mô hình (Multiple Linear, Polynomial, SVR, Decision Tree, Random Forest), thực hiện các bước sau cho **từng file notebook**:

1. **Tải dữ liệu lên**: Upload file `data.csv` vào môi trường runtime của từng notebook.
    
2. **Cập nhật đường dẫn**: Đảm bảo tên file trong code khớp với file vừa upload (ví dụ: đổi thành `data.csv`).
    
3. **Thực thi tự động**: Sử dụng tính năng **Runtime -> Run All** để chạy toàn bộ các ô lệnh `(cells)` cùng lúc nhằm tối ưu hóa thời gian.
    

## 3. Tiêu chí Đánh giá

Sử dụng **Hệ số xác định $R^2$** `(R-squared coefficient)` để so sánh các mô hình:

- Giá trị $R^2$ càng gần 1, mô hình càng chính xác.
    
- **Quy tắc chọn lọc**: Chọn mô hình có giá trị $R^2$ cao nhất.
    

## 4. Kết quả Thực nghiệm: Hồi quy Tuyến tính Đa biến

Thử nghiệm đầu tiên với mô hình **Hồi quy Tuyến tính Đa biến** `(Multiple Linear Regression)`:

- **Kết quả**: $R^2 = 0.93$.
    
- **Đánh giá**: Đây là một kết quả rất tốt. Khi quan sát vector dự đoán so với vector kết quả thực tế, các giá trị rất sát nhau.
    

---

_Ghi chú: Các bước tiếp theo sẽ tiếp tục chạy thử nghiệm trên các mô hình còn lại (Polynomial, SVR, Decision Tree, Random Forest) để tìm ra kết quả tối ưu hơn 0.93 (nếu có)._