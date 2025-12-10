Dưới đây là ghi chú học tập chi tiết được chuyển đổi từ nội dung bài giảng, tập trung vào quy trình và các công cụ thực hiện Tiền xử lý dữ liệu:

## Quy trình Tiền xử lý Dữ liệu (Data Preprocessing Workflow)

Bài học giới thiệu lộ trình thực hiện và các công cụ kỹ thuật sẽ được triển khai trong quá trình tiền xử lý dữ liệu. Quy trình này bao gồm các bước tuần tự sau:

## 1. Các bước thực hiện chính

1. **Nhập thư viện (Importing libraries)**: Thiết lập các thư viện tiêu chuẩn luôn được sử dụng trong mọi triển khai mô hình học máy.
    
2. **Nhập bộ dữ liệu (Importing the dataset)**:
    
    - Tải dữ liệu lên Google Colab.
        
    - Viết mã để đưa dữ liệu vào môi trường Python.
        
3. **Xử lý dữ liệu bị thiếu (Taking care of missing data)**:
    
    - _Vấn đề_: Các bộ dữ liệu thực tế thường không hoàn hảo (ví dụ: thiếu thông tin lương, tuổi).
        
    - _Giải pháp_: Áp dụng các kỹ thuật để xử lý các ô trống, tối ưu hóa việc huấn luyện mô hình.
        
4. **Mã hóa dữ liệu phân loại (Encoding categorical data)**:
    
    - _Vấn đề_: Máy tính cần làm việc với số, nhưng dữ liệu thường chứa chữ (ví dụ: cột `Country` chứa France, Spain; cột `Purchased` chứa Yes/No).
        
    - _Phạm vi_: Xử lý cả biến độc lập (independent variable/predictors) và biến phụ thuộc (dependent variable).
        
5. **Chia bộ dữ liệu (Splitting the dataset)**:
    
    - Chia thành 2 phần: **Tập huấn luyện (Training set)** và **Tập kiểm tra (Test set)**.
        
    - _Mục đích_:
        
        - Tập huấn luyện: Giúp mô hình hiểu các mối tương quan trong dữ liệu.
            
        - Tập kiểm tra: Đánh giá hiệu suất mô hình trên các quan sát mới (dữ liệu chưa từng thấy).
            
    - _Lợi ích_: Ngăn chặn hiện tượng **quá khớp (overfitting)** - tình trạng mô hình học quá kỹ tập huấn luyện nhưng hoạt động kém trên dữ liệu thực tế.
        
6. **Tiêu chuẩn hóa đặc trưng (Feature scaling)**:
    
    - Đưa các đặc trưng (features) về cùng một quy mô (scale).
        
    - _Lưu ý_: Không phải lúc nào cũng cần dùng, nhưng là công cụ bắt buộc phải có trong bộ công cụ tiền xử lý.
        

## 2. Hướng dẫn thiết lập môi trường thực hành

Khóa học đề cao phương pháp "Học qua hành động" (Action-based), do đó học viên sẽ không chỉ đọc mã có sẵn mà sẽ viết lại từ đầu.

**Các bước chuẩn bị trên Google Colab:**

1. **Tạo bản sao**: Vì tệp gốc ở chế độ "chỉ xem" (read-only), cần vào `File` > `Save a copy in Drive` để tạo bản sao có thể chỉnh sửa.
    
2. **Làm sạch tệp mẫu**:
    
    - Giữ lại các ô văn bản (text cells) chứa tiêu đề/cấu trúc.
        
    - Xóa toàn bộ các ô chứa mã lệnh (code cells) bằng nút thùng rác.
        
3. **Mục tiêu**: Tự tay triển khai lại (re-implement) từng dòng mã để hiểu sâu về cấu trúc và cách hoạt động của từng công cụ.
    

---

**Ghi chú**: Trong các bài học tiếp theo, chúng ta sẽ bắt đầu viết mã cho từng bước nêu trên, bắt đầu từ việc nhập thư viện.