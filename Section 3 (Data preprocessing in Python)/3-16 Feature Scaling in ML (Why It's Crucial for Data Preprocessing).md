## Chuẩn hóa đặc trưng (Feature Scaling)

## Khái niệm và Mục đích

- **Khái niệm**: Là kỹ thuật đưa tất cả các đặc trưng (features) về cùng một quy mô hoặc phạm vi giá trị.
    
- **Lý do cần thiết**:
    
    - Ngăn chặn việc các mô hình máy học (Machine Learning models) bị chi phối bởi các đặc trưng có giá trị lớn, dẫn đến việc bỏ qua các đặc trưng có giá trị nhỏ hơn.
        
    - Một số mô hình sẽ không hoạt động hiệu quả nếu các biến số có sự chênh lệch quá lớn.
        
- **Lưu ý**: Không phải mô hình nào cũng cần áp dụng kỹ thuật này.
    
    - Ví dụ: Mô hình hồi quy tuyến tính đa biến (Multiple Linear Regression) có các hệ số (coefficients) có thể tự điều chỉnh (lấy giá trị nhỏ) để bù đắp cho các biến có giá trị lớn.
        

## Các phương pháp Chuẩn hóa chính

## 1. Standardization (Chuẩn hóa Z-score)

- **Cơ chế**: Trừ mỗi giá trị cho giá trị trung bình (mean) của toàn bộ đặc trưng, sau đó chia cho độ lệch chuẩn (standard deviation).
    
- **Kết quả**: Các giá trị đặc trưng sẽ nằm trong khoảng xấp xỉ từ **-3 đến +3**.
    
- **Đánh giá**: Kỹ thuật này hoạt động tốt trong hầu hết các trường hợp.
    

## 2. Normalization (Chuẩn hóa Min-Max)

- **Cơ chế**: Trừ mỗi giá trị cho giá trị nhỏ nhất (minimum), sau đó chia cho hiệu số giữa giá trị lớn nhất (maximum) và giá trị nhỏ nhất.
    
- **Kết quả**: Các giá trị đặc trưng sẽ nằm trong khoảng từ **0 đến 1**.
    
- **Đánh giá**: Được khuyến nghị khi hầu hết các đặc trưng tuân theo phân phối chuẩn (normal distribution).
    

## Nên chọn phương pháp nào?

- **Standardization** là phương pháp được khuyến nghị sử dụng phổ biến hơn (pragmatic choice).
    
- Lý do: Nó luôn đảm bảo quá trình chuẩn hóa đặc trưng diễn ra hợp lý và cải thiện quá trình huấn luyện mô hình, bất kể phân phối của dữ liệu.
    

## Quy trình áp dụng (Implementation Logic)

Việc chuẩn hóa phải được thực hiện **sau khi** đã chia tách dữ liệu thành tập huấn luyện (Training set) và tập kiểm tra (Test set).

**Nguyên tắc thực hiện:**

1. **Fit (Học tham số)**: Chỉ thực hiện trên tập huấn luyện (`X_train`). Máy sẽ tính toán giá trị trung bình và độ lệch chuẩn của riêng `X_train`.
    
2. **Transform (Biến đổi)**: Áp dụng công thức chuẩn hóa cho cả `X_train` và `X_test`.
    

**Tại sao không Fit trên tập kiểm tra (`X_test`)?**

- `X_test` đóng vai trò là dữ liệu mới, chưa từng thấy (như dữ liệu trong thực tế/production).
    
- Nếu tính toán trung bình/độ lệch chuẩn trên `X_test`, ta đã vi phạm nguyên tắc, làm rò rỉ thông tin (data leakage).
    
- Do đó, phải dùng tham số thống kê (mean, standard deviation) của `X_train` để áp dụng quy đổi cho `X_test`.