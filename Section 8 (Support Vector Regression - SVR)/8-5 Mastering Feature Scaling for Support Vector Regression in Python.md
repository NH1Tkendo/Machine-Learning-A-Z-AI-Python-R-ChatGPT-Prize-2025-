## Feature Scaling trong SVR

Trong bài toán SVR này, quy trình xử lý dữ liệu có những điểm khác biệt quan trọng so với các mô hình trước đây (như Hồi quy tuyến tính đơn giản hay Đa biến).

## 1. Phạm vi áp dụng

- **Không chia tập dữ liệu**: Do tập dữ liệu nhỏ, ta không chia thành tập huấn luyện (training set) và tập kiểm tra (test set) mà huấn luyện trên toàn bộ dữ liệu để mô hình học được tối đa các mối tương quan.
    
- **Quy chuẩn hóa toàn bộ**: Áp dụng Feature Scaling lên toàn bộ ma trận đặc trưng $X$ thay vì chỉ `X_train` và `X_test` riêng biệt.
    

## 2. Tại sao phải quy chuẩn hóa biến phụ thuộc ($y$)?

Trong các bài học trước (ví dụ về dữ liệu mua hàng), ta không quy chuẩn hóa biến phụ thuộc ($y$) vì nó chỉ nhận giá trị nhị phân 0 hoặc 1 (đã cùng phạm vi với các biến đã quy chuẩn). Tuy nhiên, với bài toán SVR này:

- **Đặc trưng ($X$ - Level)**: Giá trị từ 1 đến 10.
    
- **Biến phụ thuộc ($y$ - Salary)**: Giá trị từ 45.000 đến 1.000.000.
    

**Vấn đề**:

- SVR không có phương trình tường minh (explicit equation) với các hệ số bù trừ như Hồi quy tuyến tính.
    
- Nếu không quy chuẩn hóa, mô hình sẽ coi trọng các giá trị lớn của $y$ và **bỏ qua (neglect)** các giá trị nhỏ của $X$.
    
- Thực tế cho thấy mô hình SVR sẽ hoạt động không hiệu quả hoặc sai hoàn toàn nếu bỏ qua bước này.
    

$\rightarrow$ **Kết luận**: Cần áp dụng Feature Scaling cho **cả ma trận đặc trưng $X$ và vector biến phụ thuộc $y$** để đưa chúng về cùng một phạm vi giá trị.

## 3. Tổng hợp quy tắc Feature Scaling

Dưới đây là hướng dẫn tổng quát để quyết định khi nào cần áp dụng Feature Scaling:

- **Biến giả (Dummy variables)** từ One-Hot Encoding: **KHÔNG** cần quy chuẩn.
    
- **Biến phụ thuộc nhị phân (0 hoặc 1)**: **KHÔNG** cần quy chuẩn.
    
- **Biến phụ thuộc có giá trị rất lớn** so với đặc trưng: **CẦN** quy chuẩn.
    
- **Khi chia tách dữ liệu**: Luôn áp dụng Feature Scaling **sau khi** đã chia thành Training set và Test set.
    

## 4. Chuyển đổi ngược (Inverse Transformation)

Một kỹ thuật quan trọng sẽ được thực hiện ở các bước sau là **nghịch đảo quy chuẩn (Inverse Feature Scaling)**.

- **Mục đích**: Để đưa các giá trị dự đoán và biểu đồ trở về thang đo gốc (Original scale).
    
- Điều này giúp ta đọc được kết quả lương thực tế (USD) thay vì con số đã bị chuẩn hóa, đồng thời trực quan hóa dữ liệu trên các trục $x, y$ với giá trị thực.