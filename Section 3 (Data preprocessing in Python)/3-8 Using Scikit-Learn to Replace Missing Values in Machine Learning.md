## Xử lý Dữ liệu bị thiếu (Handling Missing Data)

Trong các bộ dữ liệu thực tế (như file `Data.csv`), việc xuất hiện các ô trống (missing values) là rất phổ biến. Việc xử lý chúng là bắt buộc vì các mô hình học máy (Machine Learning models) thường sẽ báo lỗi nếu đầu vào chứa dữ liệu bị thiếu.

## 1. Các phương pháp tiếp cận

Có hai cách chính để xử lý dữ liệu bị thiếu:

- **Phương pháp 1: Xóa bỏ (Deletion)**
    
    - **Cách làm**: Xóa toàn bộ dòng (quan sát) chứa dữ liệu thiếu.
        
    - **Điều kiện áp dụng**: Khi bộ dữ liệu lớn và lượng dữ liệu thiếu rất nhỏ (khoảng 1%). Nếu xóa quá nhiều sẽ ảnh hưởng đến chất lượng mô hình.
        
- **Phương pháp 2: Thay thế (Imputation) - _Khuyên dùng_**
    
    - **Cách làm**: Thay thế giá trị bị thiếu bằng một giá trị thống kê của cột đó.
        
    - **Các chiến lược phổ biến**:
        
        - Trung bình (Mean) - _Phổ biến nhất_.
            
        - Trung vị (Median).
            
        - Giá trị xuất hiện nhiều nhất (Most frequent) - _Thường dùng cho dữ liệu phân loại_.
            

## 2. Công cụ sử dụng: Scikit-learn

Chúng ta sử dụng thư viện **Scikit-learn** (`sklearn`), một trong những thư viện khoa học dữ liệu mạnh mẽ nhất, để thực hiện việc thay thế dữ liệu.

- **Module**: `sklearn.impute`
    
- **Lớp (Class)**: `SimpleImputer`
    

## 3. Triển khai Mã nguồn (Python)

Quy trình bao gồm việc nhập thư viện và cấu hình công cụ `SimpleImputer` để thay thế giá trị thiếu bằng giá trị trung bình.

## Bước 1: Nhập thư viện

python

`# Nhập lớp SimpleImputer từ module impute của sklearn from sklearn.impute import SimpleImputer import numpy as np # Cần thiết để định nghĩa giá trị nan`

## Bước 2: Khởi tạo đối tượng Imputer

Tạo một đối tượng (instance) từ lớp `SimpleImputer` và cấu hình các tham số:

python

`# Tạo đối tượng imputer với chiến lược thay thế bằng trung bình imputer = SimpleImputer(missing_values=np.nan, strategy='mean')`

**Giải thích tham số:**

- `missing_values=np.nan`: Chỉ định rằng các giá trị cần thay thế là các giá trị rỗng (`nan` - not a number).
    
- `strategy='mean'`: Chỉ định phương pháp thay thế là lấy giá trị trung bình của cột chứa dữ liệu thiếu.
    

---

**Ghi chú học tập:**

> Đối tượng `imputer` vừa tạo hiện tại chỉ mới là một công cụ đã được cấu hình. Ở bước tiếp theo (trong bài học sau), chúng ta sẽ cần áp dụng công cụ này vào ma trận đặc trưng `X` để thực sự lấp đầy các ô trống.