## Quy trình xây dựng Hồi quy Đa thức (Implementation Steps)

Quy trình này bao gồm hai giai đoạn chính: tạo các đặc trưng lũy thừa (powered features) và sau đó tích hợp chúng vào một mô hình hồi quy tuyến tính.

## 1. Tạo ma trận đặc trưng đa thức (Polynomial Features Matrix)

Bước này biến đổi ma trận đặc trưng đơn lẻ ban đầu $X$ (chỉ chứa $x_1$) thành một ma trận mới `X_poly` chứa các biến $x_1$ ở các lũy thừa khác nhau.

Với bậc $N=2$, mô hình sẽ học phương trình:  
y=b0+b1x1+b2x12y = b_0 + b_1x_1 + b_2x_1^2y=b0+b1x1+b2x12

**Cách thực hiện:**

- Sử dụng lớp `PolynomialFeatures` từ thư viện `scikit-learn`.
    
- Tham số quan trọng: `degree` (bậc của đa thức). Trong ví dụ này bắt đầu với `degree=2`.
    
- Sử dụng phương thức `fit_transform` để vừa khớp dữ liệu vừa biến đổi $X$.
    

python

`from sklearn.preprocessing import PolynomialFeatures # Khởi tạo đối tượng tạo đặc trưng đa thức với bậc 2 poly_reg = PolynomialFeatures(degree = 2) # Biến đổi ma trận X ban đầu thành ma trận X_poly (chứa x1 và x1^2) X_poly = poly_reg.fit_transform(X)`

## 2. Huấn luyện mô hình Hồi quy Đa thức

Sau khi có ma trận đặc trưng mới (`X_poly`), ta coi đây là một bài toán Hồi quy Tuyến tính Đa biến thông thường (với các biến là $x_1, x_1^2, \dots$).

**Lưu ý:**

- Cần tạo một đối tượng `LinearRegression` **mới** (đặt tên là `lin_reg_2`) để phân biệt với mô hình hồi quy tuyến tính đơn giản (`lin_reg`) đã tạo trước đó.
    
- Đối tượng này sẽ được huấn luyện trên `X_poly` và `y`.
    

python

`# Tạo đối tượng hồi quy tuyến tính mới lin_reg_2 = LinearRegression() # Huấn luyện mô hình với ma trận đặc trưng đa thức và biến mục tiêu y lin_reg_2.fit(X_poly, y)`

## Tổng kết luồng dữ liệu

1. **Input:** Ma trận $X$ (chứa Levels).
    
2. **Transformation:** Qua `PolynomialFeatures` $\rightarrow$ Ma trận `X_poly` (chứa Levels, Levels$^2$).
    
3. **Modeling:** `LinearRegression` học mối quan hệ giữa `X_poly` và $y$ (Salaries).
    
4. **Result:** Mô hình phi tuyến tính được thiết lập sẵn sàng để dự đoán và trực quan hóa.