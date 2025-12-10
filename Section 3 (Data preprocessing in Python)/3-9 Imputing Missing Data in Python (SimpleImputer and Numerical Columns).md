## Áp dụng Xử lý Dữ liệu thiếu trên Ma trận Đặc trưng

Sau khi đã tạo đối tượng `imputer` (công cụ), chúng ta cần kết nối và áp dụng nó lên ma trận đặc trưng `X` để thực sự thay thế các giá trị bị thiếu. Quá trình này gồm hai bước chính: `fit` và `transform`.

## 1. Phương thức `fit`

- **Mục tiêu**: Kết nối đối tượng `imputer` với dữ liệu để tính toán (ví dụ: tính trung bình cộng của cột).
    
- **Lưu ý quan trọng**: Chỉ áp dụng trên các cột chứa dữ liệu số (numerical columns). Tránh các cột chứa chuỗi ký tự (string/text) để không gây lỗi.
    
- **Cú pháp**:
    
    python
    
    `imputer.fit(X[:, 1:3])`
    
    - `X[:, 1:3]`: Chọn tất cả các hàng và các cột từ chỉ mục 1 đến 2 (Age và Salary).
        
    - _Tại sao là 1:3?_: Vì Python loại trừ cận trên, nên `1:3` sẽ lấy cột 1 (Age) và cột 2 (Salary), loại bỏ cột 0 (Country - chứa text).
        

## 2. Phương thức `transform`

- **Mục tiêu**: Thực hiện thay thế các giá trị thiếu bằng giá trị đã tính toán từ bước `fit`.
    
- **Hành động**: Trả về phiên bản đã được cập nhật của các cột dữ liệu.
    
- **Cập nhật lại biến X**: Cần gán ngược lại kết quả trả về vào các cột tương ứng trong `X`.
    
- **Cú pháp**:
    
    python
    
    `X[:, 1:3] = imputer.transform(X[:, 1:3])`
    

## 3. Mã nguồn hoàn chỉnh

python

`# Bước 1: Kết nối imputer và tính toán giá trị trung bình trên các cột số (Age, Salary) imputer.fit(X[:, 1:3]) # Bước 2: Thay thế giá trị thiếu và cập nhật lại vào ma trận X X[:, 1:3] = imputer.transform(X[:, 1:3])`

## 4. Kiểm tra kết quả

Sau khi chạy mã xử lý, sử dụng lệnh `print(X)` để xác nhận rằng các giá trị `nan` đã biến mất.

- **Kết quả mong đợi**:
    
    - Ô chứa giá trị `nan` (trước đó là `Salary` của khách hàng Đức và `Age` bị thiếu) sẽ được thay thế bằng con số cụ thể.
        
    - Con số này chính là trung bình cộng của các giá trị còn lại trong cùng cột đó.
        

---

**Ghi chú học tập**:

> Trong thực tế làm việc với bộ dữ liệu lớn (Big Data), bạn sẽ không thể kiểm tra bằng mắt từng dòng. Quy tắc chung là luôn chọn **tất cả các cột dữ liệu số** (numerical columns) để áp dụng `imputer` nhằm đảm bảo không bỏ sót bất kỳ giá trị thiếu nào.

**Chủ đề tiếp theo**: Mã hóa dữ liệu phân loại (Encoding Categorical Data).