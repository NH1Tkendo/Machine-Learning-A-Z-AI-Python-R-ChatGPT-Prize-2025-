## Hồi quy Tuyến tính Đa biến - Nội dung Mở rộng (Bonus Content)

Đây là phần giải đáp các thắc mắc thường gặp (FAQ) về cách vận dụng mô hình vào thực tế sau khi đã huấn luyện xong.

## 1. Dự đoán cho một giá trị đơn lẻ (Single Prediction)

**Câu hỏi**: Làm thế nào để sử dụng mô hình dự đoán lợi nhuận cho **một** startup cụ thể với các thông số cho trước?

- **R&D Spend**: 160,000
    
- **Administration Spend**: 130,000
    
- **Marketing Spend**: 300,000
    
- **State**: California
    

**Cách thực hiện**:

- Phương thức `predict` luôn yêu cầu đầu vào là một mảng 2 chiều (2D array).
    
- Dữ liệu đầu vào phải tương thích với định dạng của ma trận huấn luyện $X$ (bao gồm cả các biến giả đã mã hóa).
    
- **Lưu ý về mã hóa**: Ví dụ với bang "California", nếu trong quá trình One-Hot Encoding nó được mã hóa thành `1, 0, 0` và đặt ở đầu ma trận, ta phải nhập đúng thứ tự đó.
    

python

`# Ví dụ mã nguồn dự đoán # Cấu trúc input: [[State_California, State_Florida, State_NewYork, R&D, Admin, Marketing]] # Giả định California = [1, 0, 0] print(regressor.predict([[1, 0, 0, 160000, 130000, 300000]]))`

> **Quan trọng**: Các giá trị số (160000, 130000...) có thể giữ nguyên (nếu không áp dụng Feature Scaling) hoặc phải được chuẩn hóa (nếu mô hình có áp dụng Feature Scaling). Trong bài này, Hồi quy tuyến tính đa biến không yêu cầu Feature Scaling.

## 2. Lấy phương trình hồi quy cuối cùng (Final Regression Equation)

**Câu hỏi**: Làm thế nào để trích xuất các hệ số để viết thành phương trình toán học hoàn chỉnh?

Công thức tổng quát:  
$y = b_0 + b_1x_1 + b_2x_2 + ... + b_nx_n$

**Cách thực hiện**:

- Sử dụng thuộc tính `.coef_` để lấy mảng các hệ số tương ứng với từng đặc trưng ($b_1, b_2, ...$).
    
- Sử dụng thuộc tính `.intercept_` để lấy hệ số chặn ($b_0$).
    

python

`# Lấy các hệ số hồi quy (Coefficients) - tương ứng với b1, b2, b3... print(regressor.coef_) # Lấy hệ số chặn (Intercept) - tương ứng với b0 print(regressor.intercept_)`

**Kết quả đầu ra (Ví dụ minh họa)**:  
Nếu `coef_` trả về `[86.6, -873, 786, 0.77, 0.03, 0.03]` và `intercept_` là `42467.53`, phương trình sẽ là:

Profit=42467.53+86.6×DummyState1−873×DummyState2+786×DummyState3+0.77×R&D+0.03×Admin+0.03×MarketingProfit = 42467.53 + 86.6 \times DummyState1 - 873 \times DummyState2 + 786 \times DummyState3 + 0.77 \times R\&D + 0.03 \times Admin + 0.03 \times MarketingProfit=42467.53+86.6×DummyState1−873×DummyState2+786×DummyState3+0.77×R&D+0.03×Admin+0.03×Marketing