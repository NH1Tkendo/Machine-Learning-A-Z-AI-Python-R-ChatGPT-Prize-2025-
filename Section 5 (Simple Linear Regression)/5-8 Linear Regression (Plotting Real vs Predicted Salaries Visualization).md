## Trực quan hóa kết quả (Visualization)

Sau khi huấn luyện và dự đoán, bước cuối cùng là trực quan hóa dữ liệu để đánh giá hiệu quả của mô hình. Chúng ta sẽ vẽ biểu đồ so sánh giữa giá trị thực tế và giá trị dự đoán.

## Phần 1: Trực quan hóa tập huấn luyện (Training Set)

Mục tiêu là vẽ một biểu đồ 2D trong đó:

- **Trục hoành (X-axis)**: Số năm kinh nghiệm.
    
- **Trục tung (Y-axis)**: Mức lương.
    
- **Điểm dữ liệu (Red points)**: Mức lương thực tế của nhân viên.
    
- **Đường thẳng (Blue line)**: Mức lương dự đoán theo mô hình hồi quy (đường hồi quy).
    

## Quy trình thực hiện với Matplotlib

Sử dụng module `pyplot` của thư viện `matplotlib` (đã được import với tên tắt là `plt`).

**1. Vẽ các điểm dữ liệu thực tế (Scatter plot)**  
Dùng hàm `plt.scatter` để chấm các điểm tương ứng với dữ liệu thật.

- Tọa độ X: `X_train` (Số năm kinh nghiệm trong tập huấn luyện).
    
- Tọa độ Y: `y_train` (Mức lương thực tế trong tập huấn luyện).
    
- Màu sắc: Đỏ (`color='red'`).
    

python

`plt.scatter(X_train, y_train, color='red')`

**2. Vẽ đường hồi quy dự đoán (Regression Line)**  
Dùng hàm `plt.plot` để vẽ đường thẳng biểu diễn phương trình hồi quy.

- Tọa độ X: `X_train`.
    
- Tọa độ Y: Giá trị dự đoán trên tập huấn luyện. Ta lấy giá trị này bằng cách gọi `regressor.predict(X_train)`.
    
- Màu sắc: Xanh dương (`color='blue'`).
    

python

`plt.plot(X_train, regressor.predict(X_train), color='blue')`

**3. Trang trí biểu đồ**  
Thêm tiêu đề và nhãn cho các trục để biểu đồ dễ hiểu hơn.

- Tiêu đề: `plt.title('Salary vs Experience (Training set)')`
    
- Nhãn trục X: `plt.xlabel('Years of Experience')`
    
- Nhãn trục Y: `plt.ylabel('Salary')`
    

**4. Hiển thị biểu đồ**  
Cuối cùng, dùng lệnh `plt.show()` để xuất biểu đồ ra màn hình.

python

`plt.title('Salary vs Experience (Training set)') plt.xlabel('Years of Experience') plt.ylabel('Salary') plt.show()`

## Kết quả mong đợi

Bạn sẽ thấy một biểu đồ với các điểm màu đỏ phân tán và một đường thẳng màu xanh dương đi xuyên qua đám mây điểm đó. Đường màu xanh thể hiện xu hướng tổng quát mà mô hình đã "học" được từ dữ liệu huấn luyện.