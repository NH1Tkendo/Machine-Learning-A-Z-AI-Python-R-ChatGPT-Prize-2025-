## Kiểm tra kết quả chia tập dữ liệu

Sau khi thực hiện chia dữ liệu bằng `train_test_split`, bước quan trọng tiếp theo là kiểm tra tính chính xác của các tập dữ liệu được tạo ra.

## 1. In các tập dữ liệu

Việc in ra 4 tập dữ liệu (`X_train`, `X_test`, `y_train`, `y_test`) giúp xác nhận cấu trúc và số lượng quan sát.

- **X_train (Tập huấn luyện - Đặc trưng)**:
    
    - Chứa 8 quan sát (80% của 10 mẫu ban đầu) được chọn ngẫu nhiên.
        
    - Bao gồm các cột: 3 cột biến giả (dummy variables) từ One Hot Encoding, cột Age, và cột Salary.
        
- **X_test (Tập kiểm tra - Đặc trưng)**:
    
    - Chứa 2 quan sát còn lại (20%).
        
    - Cấu trúc cột tương tự `X_train`.
        
- **y_train (Tập huấn luyện - Biến mục tiêu)**:
    
    - Chứa 8 quyết định mua hàng (0 hoặc 1) tương ứng chính xác với 8 khách hàng trong `X_train`.
        
- **y_test (Tập kiểm tra - Biến mục tiêu)**:
    
    - Chứa 2 quyết định mua hàng tương ứng với 2 khách hàng trong `X_test`.
        

## 2. Ý nghĩa của việc kiểm tra

- **Xác nhận ngẫu nhiên**: Đảm bảo dữ liệu được trộn lẫn, không lấy theo thứ tự ban đầu.
    
- **Tính tương ứng**: Đảm bảo mỗi hàng trong `X` (đặc trưng) khớp đúng với nhãn tương ứng trong `y` (kết quả). Ví dụ: Thông tin khách hàng A trong `X_train` phải khớp với quyết định mua của chính khách hàng A trong `y_train`.
    

## 3. Tổng kết giai đoạn

Đến thời điểm này, bộ công cụ tiền xử lý dữ liệu (Data Preprocessing Toolkit) đã gần hoàn thiện với các công cụ:

1. Xử lý dữ liệu thiếu (Missing Data)
    
2. Mã hóa dữ liệu phân loại (Categorical Data Encoding)
    
3. Chia tập dữ liệu (Splitting Dataset) - **Lưu ý quan trọng**: Thực hiện bước này trước khi Feature Scaling để tránh rò rỉ thông tin (information leakage).
    

Bước cuối cùng để hoàn thiện quy trình chuẩn bị dữ liệu là **Feature Scaling** (Chuẩn hóa dữ liệu), sẽ được thực hiện ngay sau đây để đảm bảo mọi biến số có cùng độ lớn, giúp mô hình máy học hoạt động hiệu quả nhất.