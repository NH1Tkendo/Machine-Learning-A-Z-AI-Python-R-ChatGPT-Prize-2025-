## 1. Huấn luyện Mô hình Hồi quy Tuyến tính (Linear Regression)

Bước này nhằm tạo ra một mô hình cơ sở để so sánh hiệu quả. Chúng ta sẽ huấn luyện trên toàn bộ tập dữ liệu (không chia train/test).

## Quy trình thực hiện

1. **Nhập thư viện:** Sử dụng `scikit-learn` để import class `LinearRegression`.
    
2. **Khởi tạo đối tượng:** Tạo một đối tượng từ class `LinearRegression`, đặt tên là `lin_reg` (để phân biệt với mô hình đa thức sau này).
    
3. **Huấn luyện mô hình:** Sử dụng phương thức `.fit()` với dữ liệu đầu vào là toàn bộ ma trận đặc trưng `X` và biến phụ thuộc `y`.
    

## Mã nguồn (Python)

python

`from sklearn.linear_model import LinearRegression # Khởi tạo đối tượng hồi quy tuyến tính lin_reg = LinearRegression() # Huấn luyện mô hình trên toàn bộ tập dữ liệu lin_reg.fit(X, y)`

---

## 2. Huấn luyện Mô hình Hồi quy Đa thức (Polynomial Regression)

Mô hình này thực chất là một dạng mở rộng của Hồi quy Tuyến tính Đa biến, nhưng các biến đầu vào là lũy thừa của cùng một biến đặc trưng ($x_1, x_1^2, x_1^n$).

## Chiến lược xây dựng

Quy trình xây dựng mô hình này gồm 2 bước chính:

1. **Tạo ma trận đặc trưng đa thức (Powered Features Matrix):** Biến đổi biến đặc trưng ban đầu $x_1$ thành một tập hợp các đặc trưng mới bao gồm $x_1, x_1^2, \dots, x_1^n$. Ma trận này được gọi là `X_poly`.
    
2. **Tích hợp vào mô hình tuyến tính:** Sử dụng một đối tượng `LinearRegression` mới để huấn luyện trên ma trận đặc trưng `X_poly` vừa tạo.
    

## Công cụ sử dụng

- **Thư viện:** `scikit-learn`
    
- **Module:** `preprocessing` (vì đây là bước tiền xử lý biến đặc trưng).
    
- **Class:** `PolynomialFeatures`.
    

## Mã nguồn - Bước chuẩn bị (Python)

python

`from sklearn.preprocessing import PolynomialFeatures # (Code tiếp theo sẽ là khởi tạo PolynomialFeatures và biến đổi X)`

**Ghi chú:** Mặc dù mô hình học được mối quan hệ phi tuyến, nhưng nó vẫn được gọi là "Polynomial _Linear_ Regression" vì phương trình dự đoán là tổ hợp tuyến tính của các hệ số với các đặc trưng lũy thừa.