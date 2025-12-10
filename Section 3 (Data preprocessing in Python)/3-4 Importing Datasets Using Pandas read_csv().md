## Nhập bộ dữ liệu (Importing a Data Set)

## Tổng quan về tập dữ liệu (Dataset)

- **Tên file**: `Data.csv`
    
- **Bối cảnh**: Dữ liệu của một công ty bán lẻ dùng để phân tích xem khách hàng nào đã mua sản phẩm.
    
- **Cấu trúc dữ liệu**:
    
    - **Hàng (Rows)**: Tương ứng với từng khách hàng cụ thể.
        
    - **Cột (Columns)**: Chứa các thông tin chi tiết gồm:
        
        - Quốc gia (Country)
            
        - Tuổi (Age)
            
        - Mức lương (Salary)
            
        - Trạng thái mua hàng (Purchased)
            

## Quy trình nhập dữ liệu bằng Python

Sử dụng thư viện Pandas để đọc file và tạo ra một **khung dữ liệu (data frame)**.

**Mã nguồn thực hiện:**

python

`# Tạo biến dataset để chứa dữ liệu # Sử dụng hàm read_csv của thư viện Pandas (viết tắt là pd) dataset = pd.read_csv('Data.csv')`

- **Giải thích**:
    
    - `dataset`: Tên biến chứa khung dữ liệu.
        
    - `pd`: Cách gọi tắt của thư viện Pandas.
        
    - `read_csv`: Hàm đọc các giá trị từ file định dạng `.csv`.
        
    - `'Data.csv'`: Tên file cần nhập (phải đặt trong dấu ngoặc kép và bao gồm cả phần mở rộng).
        

## Nguyên lý quan trọng trong Machine Learning

Trong mọi mô hình học máy, dữ liệu luôn được phân chia thành hai thực thể riêng biệt:

1. **Đặc trưng (Features)** - còn gọi là **Biến độc lập (Independent variables)**:
    
    - Là các biến chứa thông tin dùng để dự đoán kết quả.
        
    - **Vị trí**: Thường nằm ở các cột đầu tiên của tập dữ liệu.
        
    - _Trong ví dụ này_: Country, Age, Salary.
        
2. **Vectơ biến phụ thuộc (Dependent variable vector)**:
    
    - Là biến chứa kết quả mà mô hình cần dự đoán.
        
    - **Vị trí**: Thường nằm ở cột cuối cùng của tập dữ liệu.
        
    - _Trong ví dụ này_: Purchased (Đã mua hoặc chưa mua).
        

## Bước tiếp theo trong Tiền xử lý dữ liệu (Data Pre-processing)

Sau khi nhập dữ liệu vào biến `dataset`, cần tách dữ liệu thành hai biến riêng biệt để huấn luyện mô hình:

- **Biến `x`**: Chứa **ma trận đặc trưng (matrix of features)** (3 cột đầu).
    
- **Biến `y`**: Chứa **vectơ biến phụ thuộc (dependent variable vector)** (cột cuối).