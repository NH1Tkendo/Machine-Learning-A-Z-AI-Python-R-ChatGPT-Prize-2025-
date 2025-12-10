## Áp dụng Feature Scaling cho tập huấn luyện

## Chọn cột cần chuẩn hóa

Chỉ áp dụng chuẩn hóa cho các cột chứa **biến số thực** (numerical variables), không áp dụng cho **biến giả** (dummy variables).

**Xác định chỉ số cột:**

- Các cột biến giả (sau khi One-Hot Encoding) thường nằm ở đầu ma trận: index 0, 1, 2.
    
- Cột `Age` (Tuổi): index 3.
    
- Cột `Salary` (Lương): index 4.
    

**Cách chọn cột:**

- Sử dụng `[:, 3:]` để lấy **tất cả các hàng** và **các cột từ index 3 trở đi** (bao gồm Age và Salary).
    
- Cách viết này linh hoạt hơn, vì nếu có thêm nhiều cột số thực khác, nó sẽ tự động lấy tất cả mà không cần chỉnh sửa code.
    

## Phương thức Fit và Transform

## Fit (Học tham số)

- Tính toán **giá trị trung bình (mean)** và **độ lệch chuẩn (standard deviation)** của từng đặc trưng.
    
- Chỉ thực hiện trên tập huấn luyện.
    

## Transform (Biến đổi)

- Áp dụng công thức chuẩn hóa để biến đổi giá trị của các đặc trưng.
    
- Sử dụng mean và standard deviation đã được tính từ bước Fit.
    

## Fit_transform (Kết hợp)

- Thực hiện cả **Fit** và **Transform** trong một bước.
    
- Tiện lợi và hiệu quả hơn khi áp dụng cho tập huấn luyện.
    

## Mã nguồn thực hiện

python

`from sklearn.preprocessing import StandardScaler # Khởi tạo đối tượng StandardScaler sc = StandardScaler() # Áp dụng fit_transform cho các cột số thực (Age và Salary) # [:, 3:] nghĩa là: tất cả các hàng, từ cột index 3 trở đi X_train[:, 3:] = sc.fit_transform(X_train[:, 3:])`

## Giải thích cú pháp

- `X_train[:, 3:]`: Lấy tất cả hàng (`:`) và các cột từ index 3 trở đi (`3:`).
    
- `sc.fit_transform(...)`: Tính mean/std và biến đổi giá trị trong một lệnh duy nhất.
    
- Kết quả được gán lại vào chính các cột đó của `X_train`.