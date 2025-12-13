## Trực quan hóa kết quả Hồi quy (Visualizing Regression Results)

Bước này giúp đánh giá trực quan hiệu suất của mô hình bằng cách so sánh dữ liệu thực tế và đường dự đoán trên biểu đồ 2D.

## 1. Trực quan hóa Hồi quy Tuyến tính (Linear Regression)

Chúng ta sử dụng thư viện `matplotlib.pyplot` để vẽ biểu đồ so sánh giữa mức lương thực tế và mức lương do mô hình tuyến tính dự đoán.

**Mã nguồn thực hiện:**

python

`import matplotlib.pyplot as plt # 1. Vẽ các điểm dữ liệu thực tế (Real results) # Sử dụng scatter plot (biểu đồ phân tán) với màu đỏ plt.scatter(X, y, color='red') # 2. Vẽ đường dự đoán của mô hình (Predictions) # Sử dụng plot (biểu đồ đường) với màu xanh # Trục Y là kết quả dự đoán từ mô hình: lin_reg.predict(X) plt.plot(X, lin_reg.predict(X), color='blue') # 3. Trang trí biểu đồ plt.title('Truth or Bluff (Linear Regression)') # Tiêu đề plt.xlabel('Position Level') # Nhãn trục X plt.ylabel('Salary')         # Nhãn trục Y # 4. Hiển thị biểu đồ plt.show()`

## 2. Phân tích biểu đồ

Sau khi chạy đoạn mã trên, ta sẽ thu được biểu đồ với các đặc điểm sau:

- **Điểm màu đỏ:** Đại diện cho dữ liệu thực tế (Lương theo cấp bậc). Dữ liệu này phân bố theo đường cong.
    
- **Đường màu xanh:** Đại diện cho mô hình hồi quy tuyến tính. Đây là một đường thẳng.
    

**Đánh giá hiệu suất:**

- Mô hình tuyến tính **không phù hợp** (not well adapted) với tập dữ liệu này.
    
- **Sai số lớn:** Đường thẳng đi xa so với nhiều điểm dữ liệu thực tế. Ví dụ: ở các vị trí cấp cao, mức lương thực tế cao hơn rất nhiều so với dự đoán.
    
- **Rủi ro:** Nếu dùng mô hình này để đàm phán lương (bài toán "Truth or Bluff"), bạn có thể đưa ra mức lương sai lệch lớn, dẫn đến đàm phán thất bại.
    

## 3. Chuẩn bị cho Hồi quy Đa thức (Polynomial Regression)

Để khắc phục hạn chế trên, bước tiếp theo là trực quan hóa kết quả của mô hình Hồi quy Đa thức.

**Thử thách (Code Challenge):**  
Hãy suy nghĩ cách sửa đổi đoạn mã trên để vẽ được đường cong dự đoán của mô hình đa thức.

- _Gợi ý:_ Cấu trúc mã giữ nguyên, nhưng phần tham số trong hàm `predict()` cần thay đổi. Bạn không thể dùng biến `X` gốc mà phải dùng biến đã được xử lý qua đa thức.
    

_(Giải pháp chi tiết sẽ được đề cập trong phần tiếp theo)._