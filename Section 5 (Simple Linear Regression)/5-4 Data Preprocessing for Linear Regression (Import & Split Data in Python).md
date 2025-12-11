## Triển khai Hồi quy tuyến tính đơn giản trên Python

## Cấu trúc quy trình thực hiện

Quy trình triển khai mô hình bao gồm các bước chính sau:

1. Import các thư viện cần thiết.
    
2. Import bộ dữ liệu (dataset).
    
3. Chia bộ dữ liệu thành tập huấn luyện (Training set) và tập kiểm tra (Test set).
    
4. Huấn luyện mô hình Hồi quy tuyến tính đơn giản trên tập huấn luyện.
    
5. Dự đoán kết quả trên tập kiểm tra.
    
6. Trực quan hóa kết quả (trên cả tập huấn luyện và tập kiểm tra).
    

## Chuẩn bị môi trường (Google Colab)

- **Tạo bản sao**: Chọn `Save a copy in Drive` để tạo bản sao notebook có thể chỉnh sửa.
    
- **Làm sạch notebook**: Xóa nội dung các ô mã (code cells) để tự thực hành viết lại từ đầu (giữ lại các tiêu đề văn bản để theo dõi cấu trúc).
    

## Bước 1: Tiền xử lý dữ liệu (Data Pre-processing)

Sử dụng lại **mẫu code (code template)** từ phần Tiền xử lý dữ liệu để tiết kiệm thời gian và đảm bảo hiệu quả.

**Các thao tác chính:**

1. **Copy-paste code**:
    
    - Import thư viện.
        
    - Import dataset.
        
    - Chia tách dữ liệu (Splitting data).
        
2. **Điều chỉnh duy nhất**: Thay đổi tên file dữ liệu trong code thành `Salary_Data.csv`.
    

**Cơ chế hoạt động của Code Template:**

- Tự động chọn biến độc lập (features): Lấy tất cả các cột trừ cột cuối cùng.
    
- Tự động chọn biến phụ thuộc (dependent variable): Lấy cột cuối cùng.
    
- Do đó, template này hoạt động tốt cho cả Hồi quy đơn giản (1 biến) và Hồi quy đa biến (nhiều biến) mà không cần sửa đổi logic chọn cột.
    

## Thao tác tải dữ liệu lên Colab

Để code hoạt động, cần tải file dữ liệu lên môi trường Colab:

1. Nhấp vào biểu tượng **Thư mục (Folder)** ở thanh bên trái.
    
2. Đợi kết nối runtime, sau đó chọn nút **Upload**.
    
3. Truy cập đường dẫn thư mục: `Part 2 - Regression` -> `Simple Linear Regression` -> `Python`.
    
4. Chọn file `Salary_Data.csv`.
    

> **Lưu ý**: Cần upload dataset trước khi chạy các ô lệnh (cells) import dữ liệu. Sau khi upload, tiến hành chạy lần lượt các ô lệnh từ trên xuống dưới để hoàn tất giai đoạn tiền xử lý.