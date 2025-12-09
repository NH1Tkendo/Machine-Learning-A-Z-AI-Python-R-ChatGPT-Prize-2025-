## Tầm quan trọng của việc chia tập dữ liệu (Splitting the Data Set)

Việc chia tập dữ liệu thành tập huấn luyện và tập kiểm tra là một bước thiết yếu trong quy trình xây dựng mô hình học máy để đảm bảo tính khách quan khi đánh giá hiệu suất.

![[TrainingSet-TestSet.png]]
## Ví dụ minh họa

Giả sử bạn cần giải quyết bài toán dự đoán giá xe hơi với dữ liệu gồm 20 chiếc xe:

- **Biến phụ thuộc (Dependent variable)**: Giá bán của xe.
    
- **Biến độc lập (Independent variables)**: Số dặm đã đi (mileage) và tuổi của xe (age).
    

## Quy trình phân chia dữ liệu

Việc phân chia thường được thực hiện trước khi bắt đầu xây dựng mô hình, với tỷ lệ phổ biến là **80/20**:

- **Tập huấn luyện (Training set)**: Chiếm khoảng **80%** dữ liệu (tương đương 16 chiếc xe).
    
    - _Mục đích_: Dùng để xây dựng và huấn luyện mô hình (ví dụ: xây dựng phương trình hồi quy tuyến tính).
        
- **Tập kiểm tra (Test set)**: Chiếm khoảng **20%** dữ liệu (tương đương 4 chiếc xe).
    
    - _Mục đích_: Được tách riêng hoàn toàn và mô hình không có thông tin gì về dữ liệu này trong quá trình huấn luyện.
        

## Cách thức đánh giá mô hình

Sau khi mô hình được xây dựng trên tập huấn luyện, quy trình đánh giá diễn ra như sau:

1. **Áp dụng mô hình**: Đưa dữ liệu từ _tập kiểm tra_ vào mô hình để tạo ra các dự đoán về giá.
    
2. **So sánh**: Đối chiếu **giá trị dự đoán (predicted values)** với **giá trị thực tế (actual values)** (vì đây là dữ liệu lịch sử nên ta đã biết giá bán thật của xe).
    
3. **Kết luận**:
    
    - Đánh giá xem mô hình hoạt động tốt hay không dựa trên sự chênh lệch giữa dự đoán và thực tế.
        
    - Xác định xem có cần cải thiện mô hình hay không.