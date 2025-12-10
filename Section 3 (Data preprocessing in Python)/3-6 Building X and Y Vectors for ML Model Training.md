Dưới đây là phần tiếp theo của ghi chú học tập, tập trung vào việc tạo vectơ biến phụ thuộc và quy trình thực thi kiểm tra dữ liệu.

---

## Tạo Vectơ Biến Phụ thuộc (Dependent Variable Vector - y)

Sau khi đã có ma trận đặc trưng ($X$), bước tiếp theo là tách cột dữ liệu cuối cùng (kết quả/nhãn) thành một vectơ riêng biệt, thường được ký hiệu là `y`.

## Nguyên lý

- Biến phụ thuộc thường nằm ở **cột cuối cùng** của bộ dữ liệu.
    
- Đây là giá trị mà mô hình máy học cần dự đoán (ví dụ: Khách hàng có mua hàng hay không?).
    

## Cú pháp lệnh

python

`y = dataset.iloc[:, -1].values`

## Giải thích sự khác biệt với X

- **Phần hàng (`:`)**: Vẫn lấy toàn bộ các hàng như khi tạo $X$.
    
- **Phần cột (`-1`)**:
    
    - Khác với $X$ (dùng `:-1` để tạo phạm vi), ở đây ta chỉ dùng `-1`.
        
    - `-1` chỉ định chính xác **một cột duy nhất** là cột cuối cùng.
        
    - Không dùng dấu hai chấm (`:`) vì ta không lấy một khoảng (range) mà lấy một vectơ đơn lẻ.
        

---

## Thực thi và Kiểm tra Dữ liệu trên Google Colab

Để đảm bảo mã nguồn hoạt động đúng, cần thực hiện quy trình tải dữ liệu và in kết quả kiểm tra.

## 1. Tải bộ dữ liệu lên môi trường (Upload Dataset)

Trước khi chạy lệnh `read_csv`, file dữ liệu phải có sẵn trong hệ thống:

1. Nhấn vào biểu tượng thư mục **Files** ở thanh bên trái.
    
2. Chọn **Upload**.
    
3. Tìm đến thư mục chứa file `Data.csv` (trong thư mục _Part 1 - Data Preprocessing_) và tải lên.
    

## 2. In kết quả kiểm tra (Print)

Sử dụng hàm `print()` để xác minh cấu trúc dữ liệu sau khi tách.

python

`# Kiểm tra Ma trận đặc trưng print(X) # Kiểm tra Vectơ biến phụ thuộc print(y)`

**Kết quả mong đợi:**

- **`print(X)`**: Hiển thị mảng chứa các cột: Country, Age, Salary (đã loại bỏ cột Purchased).
    
- **`print(y)`**: Hiển thị vectơ chứa các giá trị quyết định: No, Yes, No... (đúng thứ tự tương ứng với $X$).
    

---

## Ghi chú thêm: Tại sao phải tách X và y?

Bạn có thể thắc mắc tại sao không nạp thẳng toàn bộ bộ dữ liệu vào mô hình?

- **Lý do kỹ thuật**: Hầu hết các thư viện và lớp (classes) xây dựng mô hình máy học (Machine Learning models) được thiết kế để nhận đầu vào là hai thực thể riêng biệt:
    
    1. **Đầu vào (Inputs/Features)**: Dữ liệu dùng để học ($X$).
        
    2. **Đầu ra (Output/Target)**: Kết quả cần dự đoán ($y$).
        
- Việc tách biệt này là tiêu chuẩn bắt buộc trong quy trình xây dựng mô hình.
    

---

**Bước tiếp theo:** Xử lý dữ liệu bị thiếu (Missing Data) - ví dụ các ô trống trong file CSV.