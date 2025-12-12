Đây là ghi chú học tập được tổng hợp từ nội dung bài giảng của bạn:

## Huấn luyện mô hình Hồi quy Tuyến tính Đa biến (Multiple Linear Regression)

## Giải đáp các thắc mắc thường gặp

Trước khi huấn luyện mô hình, có hai vấn đề kỹ thuật quan trọng cần làm rõ:

## 1. Bẫy biến giả (Dummy Variable Trap)

- **Câu hỏi**: Chúng ta có cần phải xử lý thủ công để tránh bẫy biến giả không?
    
- **Trả lời**: **Không**.
    
- **Lý do**:
    
    - Lớp `LinearRegression` trong thư viện được sử dụng sẽ tự động xử lý vấn đề này.
        
    - Mặc dù khi mã hóa One-Hot, chúng ta tạo ra các cột dư thừa (ví dụ: cột thứ 3 có thể suy ra từ 2 cột đầu), nhưng thư viện sẽ tự động loại bỏ hoặc xử lý sự phụ thuộc tuyến tính này.
        
    - Người dùng không cần phải xóa thủ công một cột biến giả.
        

## 2. Chọn lọc đặc trưng (Feature Selection / Backward Elimination)

- **Câu hỏi**: Chúng ta có cần áp dụng kỹ thuật loại bỏ ngược (Backward Elimination) để chọn các đặc trưng có giá trị P (P-values) tốt nhất không?
    
- **Trả lời**: **Không bắt buộc** trong giai đoạn này.
    
- **Lý do**:
    
    - Lớp `LinearRegression` cũng tự động xác định các đặc trưng có ý nghĩa thống kê nhất để dự đoán biến phụ thuộc với độ chính xác cao nhất.
        
    - Trong thực tế công việc, mục tiêu là sự hiệu quả. Thay vì tốn thời gian chọn lọc thủ công (như Backward Elimination), ta nên chạy mô hình, lấy độ chính xác và so sánh với các mô hình khác (Quy trình Lựa chọn Mô hình - Model Selection).
        

## Xây dựng và Huấn luyện Mô hình

## Đặc điểm của lớp `LinearRegression`

- Sử dụng cùng một lớp `LinearRegression` từ thư viện Scikit-Learn giống như bài toán Hồi quy Tuyến tính Đơn biến (Simple Linear Regression).
    
- Lớp này đủ thông minh để nhận diện đầu vào có nhiều đặc trưng (Multiple features) và tự động thực hiện hồi quy đa biến.
    
- Nó sẽ tự động học mối tương quan giữa tất cả các đặc trưng và biến mục tiêu (lợi nhuận).
    

## Mã nguồn thực hiện (Python)

Quy trình thực hiện bao gồm 3 bước chính:

1. **Import thư viện**: Từ `sklearn.linear_model`
    
2. **Khởi tạo đối tượng**: Tạo biến `regressor` là một instance của lớp `LinearRegression`.
    
3. **Tham số**: Giữ nguyên các giá trị mặc định, không cần truyền tham số vào trong dấu ngoặc đơn `()`.
    

python

`# 1. Nhập lớp LinearRegression từ module linear_model của thư viện Scikit-Learn from sklearn.linear_model import LinearRegression # 2. Khởi tạo mô hình (Tạo một đối tượng từ lớp LinearRegression) regressor = LinearRegression() # Ghi chú: Không cần truyền tham số nào vào trong LinearRegression()  # vì ta sử dụng các giá trị mặc định cho mô hình cơ bản.`

## Tổng kết

- Việc sử dụng các thư viện hiện đại (như Scikit-Learn) giúp tự động hóa nhiều bước phức tạp (tránh bẫy biến giả, chọn lọc đặc trưng cơ bản).
    
- Code triển khai Hồi quy Tuyến tính Đa biến gần như giống hệt Hồi quy Tuyến tính Đơn biến, sự khác biệt nằm ở dữ liệu đầu vào ($X$ có nhiều cột hơn).