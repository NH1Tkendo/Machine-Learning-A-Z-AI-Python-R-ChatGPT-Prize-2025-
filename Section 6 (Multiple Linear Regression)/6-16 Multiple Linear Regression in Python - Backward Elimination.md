## Hồi quy Tuyến tính Đa biến - Kỹ thuật Loại bỏ Ngược (Backward Elimination)

## Tổng quan

Đây là kỹ thuật chọn lọc đặc trưng thủ công nhằm xác định các biến có ý nghĩa thống kê cao nhất (statistically significant).

- **Lưu ý**: Trong Python hiện đại, việc này là **tùy chọn (optional)**. Thư viện `Scikit-Learn` (lớp `LinearRegression`) đã tự động chọn lọc các đặc trưng tốt nhất khi huấn luyện mô hình dự đoán.
    
- **Mục đích**: Học cách thực hiện thủ công giúp hiểu sâu hơn về mối quan hệ thống kê giữa các biến.
    

## Các bước chuẩn bị đặc biệt

Khác với quy trình chuẩn của `Scikit-Learn`, khi thực hiện thủ công với thư viện `statsmodels`, ta cần lưu ý:

1. **Xử lý Bẫy biến giả (Dummy Variable Trap) thủ công**:  
    Cần loại bỏ thủ công một cột biến giả để tránh đa cộng tuyến hoàn hảo (nếu thư viện không tự xử lý).
    
    python
    
    `# Loại bỏ cột đầu tiên sau khi One-Hot Encoding X = X[:, 1:]`
    
2. **Thêm hệ số chặn (Intercept)**:  
    Thư viện `statsmodels` không tự động thêm hằng số $b_0$ vào phương trình $y = b_0 + b_1x_1 + ... + b_nx_n$. Ta cần thêm một cột toàn số `1` vào ma trận đặc trưng $X$ (tương ứng với $x_0 = 1$).
    

## Mã nguồn thực hiện (Full Code)

Dưới đây là quy trình đầy đủ bao gồm tiền xử lý và các bước lặp của kỹ thuật Loại bỏ Ngược:

python

`# 1. Nhập thư viện và dữ liệu import numpy as np import matplotlib.pyplot as plt import pandas as pd import statsmodels.api as sm dataset = pd.read_csv('50_Startups.csv') X = dataset.iloc[:, :-1].values y = dataset.iloc[:, -1].values # 2. Mã hóa dữ liệu phân loại (Encoding) from sklearn.compose import ColumnTransformer from sklearn.preprocessing import OneHotEncoder ct = ColumnTransformer(transformers=[('encoder', OneHotEncoder(), [3])], remainder='passthrough') X = np.array(ct.fit_transform(X)) # 3. Tránh bẫy biến giả (Thủ công) X = X[:, 1:] # 4. Phân chia tập dữ liệu (Train/Test Split) from sklearn.model_selection import train_test_split X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 0) # 5. Huấn luyện mô hình cơ bản (Scikit-Learn) from sklearn.linear_model import LinearRegression regressor = LinearRegression() regressor.fit(X_train, y_train) # --- BẮT ĐẦU QUY TRÌNH BACKWARD ELIMINATION --- # Bước A: Thêm cột số 1 vào đầu ma trận X (để đại diện cho b0) # np.ones((50, 1)) tạo cột 50 hàng chứa số 1 # axis = 1 là nối theo chiều ngang X = np.append(arr = np.ones((50, 1)).astype(int), values = X, axis = 1) # Bước B: Khởi tạo ma trận tối ưu (X_opt) chứa tất cả các biến ban đầu # Giả sử ta có 6 cột (0 đến 5) X_opt = X[:, [0, 1, 2, 3, 4, 5]] X_opt = X_opt.astype(np.float64) # Bước C: Thực hiện lặp và kiểm tra P-value # Lần 1: Chạy với tất cả biến regressor_OLS = sm.OLS(endog = y, exog = X_opt).fit() regressor_OLS.summary()  # -> Quan sát bảng summary, tìm biến có P-value cao nhất (ví dụ > 0.05) để loại bỏ # Lần 2: Giả sử biến ở index 2 có P-value cao nhất, ta loại bỏ nó X_opt = X[:, [0, 1, 3, 4, 5]] X_opt = X_opt.astype(np.float64) regressor_OLS = sm.OLS(endog = y, exog = X_opt).fit() regressor_OLS.summary() # Lần 3: Tiếp tục loại bỏ biến (ví dụ biến index 1) X_opt = X[:, [0, 3, 4, 5]] X_opt = X_opt.astype(np.float64) regressor_OLS = sm.OLS(endog = y, exog = X_opt).fit() regressor_OLS.summary() # Lần 4: Tiếp tục loại bỏ biến (ví dụ biến index 4) X_opt = X[:, [0, 3, 5]] X_opt = X_opt.astype(np.float64) regressor_OLS = sm.OLS(endog = y, exog = X_opt).fit() regressor_OLS.summary() # Lần 5: Tiếp tục loại bỏ biến (ví dụ biến index 5) # Chỉ còn lại biến index 0 (hằng số) và biến index 3 (ví dụ: R&D Spend) X_opt = X[:, [0, 3]] X_opt = X_opt.astype(np.float64) regressor_OLS = sm.OLS(endog = y, exog = X_opt).fit() regressor_OLS.summary() # Kết thúc khi không còn biến nào có P-value > mức ý nghĩa (SL - thường là 0.05)`

## Giải thích các thuật ngữ trong Code

- `sm.OLS`: Ordinary Least Squares (Phương pháp bình phương tối thiểu thông thường) - thuật toán cốt lõi của hồi quy tuyến tính.
    
- `endog`: Biến nội sinh (biến phụ thuộc $y$).
    
- `exog`: Biến ngoại sinh (các biến độc lập $X$).
    
- `fit()`: Huấn luyện mô hình.
    
- `summary()`: Hiển thị bảng thống kê chi tiết, bao gồm P-value, R-squared, hệ số hồi quy...