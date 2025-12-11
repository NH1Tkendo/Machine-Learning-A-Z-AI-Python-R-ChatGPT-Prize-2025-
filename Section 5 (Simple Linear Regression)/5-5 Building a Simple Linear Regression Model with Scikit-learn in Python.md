## Huấn luyện mô hình Hồi quy Tuyến tính Đơn giản (Training the Simple Linear Regression Model)

## Thư viện sử dụng

Để xây dựng mô hình một cách nhanh chóng và hiệu quả, chúng ta sẽ sử dụng thư viện **Scikit-learn** thay vì viết mã từ đầu (scratch).

**Quy trình import thư viện:**

1. Từ thư viện `sklearn` (Scikit-learn).
    
2. Truy cập module `linear_model`.
    
3. Import lớp `LinearRegression`.
    

python

`from sklearn.linear_model import LinearRegression`

## Khởi tạo đối tượng mô hình

Chúng ta sẽ tạo một đối tượng (instance) từ lớp `LinearRegression`. Đối tượng này chính là mô hình hồi quy tuyến tính đơn giản của chúng ta.

- **Tên biến**: Đặt tên là `regressor` (vì đây là bài toán hồi quy).
    
- **Phân biệt Hồi quy (Regression) và Phân loại (Classification)**:
    
    - _Hồi quy_: Dự đoán một giá trị thực liên tục (ví dụ: mức lương).
        
    - _Phân loại_: Dự đoán một danh mục hoặc lớp (sẽ học ở phần 3).
        

**Mã khởi tạo mô hình:**

python

`regressor = LinearRegression()`

_Lưu ý: Đối với hồi quy tuyến tính đơn giản, thường không cần truyền tham số vào trong ngoặc `()`._

## Kết nối với tập dữ liệu huấn luyện

Sau khi khởi tạo, mô hình mới chỉ là một bộ khung "rỗng". Cần kết nối mô hình với tập huấn luyện (training set) để nó "học" từ dữ liệu.

- **Hàm thực hiện**: Sử dụng phương thức `fit`.
    
- **Chức năng**: Kết nối mô hình với dữ liệu để tiến hành quá trình huấn luyện (training).