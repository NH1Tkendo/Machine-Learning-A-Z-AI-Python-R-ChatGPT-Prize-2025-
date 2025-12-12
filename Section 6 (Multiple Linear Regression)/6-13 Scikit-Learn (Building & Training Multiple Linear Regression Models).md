## Huấn luyện Mô hình và Chiến lược Đánh giá

## Huấn luyện Mô hình trên Tập huấn luyện

Sau khi khởi tạo đối tượng mô hình, bước tiếp theo là "làm cho mô hình thông minh hơn" bằng cách huấn luyện nó trên dữ liệu đã chuẩn bị.

- **Phương thức sử dụng**: `fit()`
    
- **Tham số đầu vào**:
    
    - `X_train`: Ma trận các đặc trưng của tập huấn luyện.
        
    - `y_train`: Vectơ biến phụ thuộc (lợi nhuận) của tập huấn luyện.
        
- **Mục tiêu**: Giúp mô hình học và hiểu được các mối tương quan (correlations) giữa các loại chi phí (R&D, Marketing, Admin...) và lợi nhuận thu được.
    

python

`# Huấn luyện mô hình Hồi quy tuyến tính đa biến trên tập huấn luyện regressor.fit(X_train, y_train)`

## Tổng kết ưu điểm của lớp LinearRegression

Lớp `LinearRegression` trong thư viện Scikit-Learn giúp đơn giản hóa quy trình xây dựng mô hình nhờ các tính năng tự động:

- **Tự động xử lý Bẫy biến giả (Dummy Variable Trap)**: Không cần loại bỏ thủ công các cột biến giả dư thừa.
    
- **Tự động chọn lọc đặc trưng (Feature Selection)**: Tự động xác định các đặc trưng có ý nghĩa thống kê cao nhất (dựa trên P-value) để dự đoán chính xác, người dùng không cần can thiệp thủ công.
    

## Chiến lược đánh giá kết quả trên Tập kiểm tra (Test Set)

Khác với Hồi quy Tuyến tính Đơn biến, việc đánh giá Hồi quy Tuyến tính Đa biến có sự thay đổi về phương pháp trực quan hóa.

- **Hạn chế về trực quan hóa**:
    
    - Do mô hình có nhiều đặc trưng (4 đặc trưng trong bài toán này), việc vẽ biểu đồ là không khả thi.
        
    - Để vẽ được, ta cần một không gian 5 chiều (4 chiều cho đặc trưng + 1 chiều cho biến phụ thuộc), điều này nằm ngoài khả năng nhận thức thị giác của con người.
        
- **Phương pháp thay thế**: So sánh hai vectơ số liệu.
    
    1. **Vectơ lợi nhuận thực tế (Real profit / Ground truth)**: Lấy từ tập kiểm tra ($y_test$). Với tập dữ liệu 50 công ty và tỷ lệ test 20%, vectơ này sẽ chứa 10 giá trị thực tế.
        
    2. **Vectơ lợi nhuận dự đoán (Predicted profit)**: Kết quả do mô hình dự đoán từ các đặc trưng của tập kiểm tra ($y_pred$).
        
- **Cách đánh giá**: Đặt hai vectơ cạnh nhau để so sánh trực tiếp xem giá trị dự đoán gần với giá trị thực tế đến mức nào. Các chỉ số đánh giá hiệu suất cụ thể (metrics) sẽ được giới thiệu ở các phần sau.