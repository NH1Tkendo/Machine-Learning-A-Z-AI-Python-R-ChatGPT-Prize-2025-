## Áp Dụng Feature Scaling cho SVR

## Tại sao cần 2 đối tượng StandardScaler riêng biệt?

Khi thực hiện quy chuẩn hóa (Standardization) cho cả ma trận đặc trưng $X$ (Position Levels) và biến phụ thuộc $y$ (Salaries), ta **không thể** dùng chung một đối tượng `StandardScaler`.

- **Lý do**:
    
    - Phương thức `.fit()` sẽ tính toán giá trị trung bình (mean) và độ lệch chuẩn (standard deviation) của dữ liệu đầu vào.
        
    - Giá trị trung bình và độ lệch chuẩn của **Position Levels** (từ 1-10) hoàn toàn khác với **Salaries** (từ 45k-1M).
        
    - Nếu dùng chung, bộ tham số quy chuẩn sẽ bị sai lệch.
        

$\rightarrow$ **Giải pháp**: Cần tạo 2 đối tượng Scaler riêng biệt: `sc_X` cho $X$ và `sc_y` cho $y$.

## Mã nguồn thực hiện

python

`from sklearn.preprocessing import StandardScaler # 1. Scaling cho ma trận đặc trưng X sc_X = StandardScaler() X = sc_X.fit_transform(X) # 2. Scaling cho biến phụ thuộc y sc_y = StandardScaler() y = sc_y.fit_transform(y)`

## Kết quả sau khi Scaling

Sử dụng lệnh `print(X)` và `print(y)` để kiểm tra dữ liệu sau biến đổi:

- **Với X (Position Levels)**:
    
    - Các giá trị được chuyển về khoảng từ khoảng -1.5 đến +1.5.
        
    - Ví dụ: Level 1 $\approx$ -1.5, Level 10 $\approx$ +1.56.
        
- **Với y (Salaries)**:
    
    - Các giá trị được chuyển về khoảng từ khoảng -0.7 đến +2.6.
        
    - Ví dụ: 45,000 $\approx$ -0.7, 1,000,000 $\approx$ +2.64.
        

**Nhận xét**:

- Sau khi quy chuẩn hóa, cả $X$ và $y$ đều nằm trong một phạm vi giá trị tương đương nhau (thường là khoảng -3 đến +3 đối với Standardization).
    
- Điều này đảm bảo mô hình SVR sẽ không bị lệch (bias) về phía biến có giá trị lớn hơn.