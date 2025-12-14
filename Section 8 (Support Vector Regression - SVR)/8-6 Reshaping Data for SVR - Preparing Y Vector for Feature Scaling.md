## Chuẩn bị dữ liệu cho Feature Scaling

## 1. Kiểm tra định dạng dữ liệu hiện tại

Trước khi biến đổi, cần kiểm tra định dạng của ma trận đặc trưng $X$ và vector biến phụ thuộc $y$.

- **In $X$**: Là một mảng 2 chiều (2D Array) chứa các giá trị mức độ vị trí (Level) từ 1 đến 10. Được nhận diện qua dấu ngoặc vuông kép `[[...]]`.
    
- **In $y$**: Là một vector 1 chiều (1D Vector) chứa các mức lương tương ứng.
    

## 2. Vấn đề với định dạng của $y$

- Class `StandardScaler` trong thư viện Scikit-Learn **yêu cầu đầu vào là mảng 2 chiều (2D Array)**.
    
- Nếu truyền $y$ ở dạng vector 1 chiều vào phương thức `fit_transform`, chương trình sẽ báo lỗi.
    
- **Giải pháp**: Cần chuyển đổi (reshape) $y$ từ vector 1 chiều thành mảng 2 chiều với các giá trị được xếp theo cột dọc.
    

## 3. Kỹ thuật Reshape $y$

Sử dụng hàm `.reshape()` để thay đổi kích thước mảng.

**Mã nguồn:**

python

`y = y.reshape(len(y), 1)`

**Giải thích tham số:**

- `len(y)`: Số lượng hàng (rows). Bằng tổng số phần tử của $y$ (số lượng mức lương).
    
- `1`: Số lượng cột (columns). Ta muốn các giá trị xếp thành 1 cột dọc.
    

## 4. Kết quả mong đợi sau khi Reshape

Sau khi biến đổi và in lại biến $y$, ta cần kiểm tra 2 yếu tố:

- **Cấu trúc 2D**: Xuất hiện dấu ngoặc vuông kép `[[...]]` bao quanh dữ liệu.
    
- **Hiển thị dọc**: Các giá trị lương được xếp chồng lên nhau theo chiều dọc, tương tự như cấu trúc của ma trận $X$.
    

Lúc này, dữ liệu đã sẵn sàng để đưa vào `StandardScaler` cho bước Feature Scaling tiếp theo.