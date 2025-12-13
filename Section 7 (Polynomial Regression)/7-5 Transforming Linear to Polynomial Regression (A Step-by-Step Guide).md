## Xây dựng Mô hình Hồi quy Đa thức (Polynomial Regression Implementation)

Quá trình xây dựng mô hình này khác với hồi quy tuyến tính thông thường ở chỗ nó yêu cầu một bước trung gian: biến đổi các đặc trưng đầu vào thành các lũy thừa.

## 1. Quy trình thực hiện

Quy trình gồm 2 bước chính:

1. **Chuẩn bị Ma trận đặc trưng đa thức (Matrix of Powered Features):** Sử dụng `PolynomialFeatures` để tạo ra một ma trận mới chứa $x_1, x_1^2, x_1^n$.
    
2. **Tích hợp vào Hồi quy Tuyến tính:** Sử dụng một đối tượng `LinearRegression` mới để học mối quan hệ giữa ma trận đặc trưng đa thức này và biến mục tiêu $y$.
    

## 2. Chi tiết các bước và Mã nguồn

## Bước 1: Tạo ma trận đặc trưng $X_{poly}$

Chúng ta sử dụng lớp `PolynomialFeatures`.

- **Tham số `degree`:** Xác định bậc cao nhất của đa thức ($n$). Trong ví dụ này, ta bắt đầu với $n=2$.
    
- **Phương trình mô hình (bậc 2):**  
    y=b0+b1x1+b2x12y = b_0 + b_1x_1 + b_2x_1^2y=b0+b1x1+b2x12
    
- **Phương thức `fit_transform`:** Vừa khớp dữ liệu vừa biến đổi ma trận $X$ ban đầu (chỉ chứa $x_1$) thành ma trận $X_{poly}$ (chứa $x_1$ và $x_1^2$).
    

## Bước 2: Huấn luyện mô hình

Chúng ta cần tạo một đối tượng hồi quy mới (đặt tên là `lin_reg_2` để phân biệt với `lin_reg` của hồi quy tuyến tính đơn).

- Đối tượng này sẽ được huấn luyện (`fit`) trên `X_poly` và `y`.
    

## Đoạn mã thực thi (Python)

python

`# 1. Nhập class PolynomialFeatures (đã thực hiện ở bài trước) from sklearn.preprocessing import PolynomialFeatures # 2. Tạo đối tượng quy định bậc của đa thức (bắt đầu với bậc 2) poly_reg = PolynomialFeatures(degree = 2) # 3. Biến đổi ma trận đặc trưng X thành ma trận đa thức X_poly # X_poly lúc này sẽ chứa các cột: [1, x_1, x_1^2] (cột 1 là hệ số bias b0) X_poly = poly_reg.fit_transform(X) # 4. Tạo mô hình Linear Regression mới để xử lý các đặc trưng đa thức lin_reg_2 = LinearRegression() # 5. Huấn luyện mô hình trên tập dữ liệu đã biến đổi lin_reg_2.fit(X_poly, y)`

## Lưu ý quan trọng

- **`lin_reg` vs `lin_reg_2`:**
    
    - `lin_reg`: Là mô hình Hồi quy Tuyến tính Đơn (Simple Linear Regression), học trực tiếp trên $X$.
        
    - `lin_reg_2`: Là mô hình Hồi quy Đa thức, học trên $X_{poly}$.
        
- **Bản chất mô hình:** Mặc dù đường cong là phi tuyến tính, nhưng mô hình `lin_reg_2` vẫn thuộc lớp "Linear Regression" vì nó coi $x_1$ và $x_1^2$ là hai biến độc lập trong một tổ hợp tuyến tính.