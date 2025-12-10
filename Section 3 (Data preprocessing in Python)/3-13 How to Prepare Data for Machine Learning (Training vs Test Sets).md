## Chia tập dữ liệu và Chuẩn hóa (Splitting & Feature Scaling)

Đây là bước quan trọng để chuẩn bị dữ liệu trước khi đưa vào mô hình máy học, đặc biệt là việc xác định đúng thứ tự thực hiện giữa hai công đoạn này.

## Quy tắc về thứ tự thực hiện

Một trong những câu hỏi phổ biến nhất trong khoa học dữ liệu là: _"Nên thực hiện chuẩn hóa dữ liệu trước hay sau khi chia tập dữ liệu?"_

- **Câu trả lời chính xác**: Phải thực hiện chuẩn hóa (Feature Scaling) **SAU KHI** chia tập dữ liệu thành tập huấn luyện và tập kiểm tra.
    
- **Thứ tự**: `Splitting Data` → `Feature Scaling`.
    

## Khái niệm cơ bản

- **Chia tập dữ liệu (Splitting the dataset)**: Tách dữ liệu thành 2 phần riêng biệt:
    
    - **Tập huấn luyện (Training set)**: Dùng để huấn luyện mô hình trên các quan sát hiện có.
        
    - **Tập kiểm tra (Test set)**: Dùng để đánh giá hiệu suất mô hình trên các quan sát mới (đại diện cho dữ liệu thực tế trong tương lai).
        
- **Chuẩn hóa dữ liệu (Feature Scaling)**: Đưa tất cả các biến (features) về cùng một phạm vi giá trị (scale). Điều này ngăn chặn việc một đặc trưng có giá trị lớn lấn át các đặc trưng khác, khiến mô hình bỏ qua chúng.
    

## Tại sao phải Chuẩn hóa SAU khi chia dữ liệu?

Lý do cốt lõi liên quan đến việc ngăn chặn **Rò rỉ thông tin (Information Leakage)**.

1. **Bản chất của Test set**: Tập kiểm tra phải được xem là dữ liệu hoàn toàn mới, dữ liệu "tương lai" mà mô hình chưa từng được biết đến trong quá trình huấn luyện.
    
2. **Cơ chế của Chuẩn hóa**: Các kỹ thuật chuẩn hóa thường tính toán dựa trên **giá trị trung bình (mean)** và **độ lệch chuẩn (standard deviation)** của dữ liệu.
    
3. **Hậu quả nếu làm sai thứ tự (Chuẩn hóa trước)**:
    
    - Nếu chuẩn hóa toàn bộ tập dữ liệu trước khi chia, bạn sẽ tính toán mean và standard deviation dựa trên cả dữ liệu của tập kiểm tra.
        
    - Điều này có nghĩa là mô hình đã "nhìn thấy" và lấy thông tin từ tập kiểm tra (thứ mà lẽ ra nó không được phép biết).
        
    - Đây gọi là **Rò rỉ thông tin (Information Leakage)**, làm sai lệch khả năng đánh giá thực tế của mô hình.
        

**Kết luận**: Luôn chia dữ liệu trước, sau đó mới tính toán các tham số chuẩn hóa dựa trên _Tập huấn luyện_ và áp dụng nó cho cả _Tập huấn luyện_ và _Tập kiểm tra_.