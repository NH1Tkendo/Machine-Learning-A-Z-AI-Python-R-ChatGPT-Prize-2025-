Dưới đây là nội dung được chuyển đổi thành ghi chú học tập định dạng Markdown, tối ưu cho Obsidian:

---

## Tạo Ma trận Đặc trưng (Matrix of Features - X)

Trong quá trình tiền xử lý dữ liệu, bước đầu tiên là tách bộ dữ liệu thành hai phần: ma trận chứa các biến độc lập (features) và vectơ chứa biến phụ thuộc. Phần này hướng dẫn cách tạo **ma trận đặc trưng (Matrix of Features)**, thường được ký hiệu là `X`.

## Nguyên lý chung

- Ma trận `X` chứa tất cả các dữ liệu của các cột biến độc lập.
    
- Thông thường, trong một bộ dữ liệu chuẩn, các cột tính năng (features) nằm ở đầu, và cột biến phụ thuộc (dependent variable) nằm ở cuối cùng.
    
- **Mục tiêu**: Lấy tất cả các hàng và tất cả các cột, **trừ cột cuối cùng**.
    

## Phương pháp thực hiện

Sử dụng hàm `iloc` (index locate) của thư viện Pandas để trích xuất dữ liệu dựa trên chỉ mục (indexes).

## Cú pháp lệnh

python

`X = dataset.iloc[:, :-1].values`

## Giải thích chi tiết cú pháp

1. **`dataset`**: Biến chứa bộ dữ liệu đã được nhập vào trước đó.
    
2. **`.iloc`**: Hàm dùng để định vị và lấy dữ liệu dựa trên chỉ mục của hàng và cột.
    
3. **`[` hàng `,` cột `]`**: Cấu trúc bên trong `iloc` được chia làm hai phần, ngăn cách bởi dấu phẩy.
    
    - **Phần hàng (`:` )**:
        
        - Dấu hai chấm đại diện cho một phạm vi (range).
            
        - Khi không ghi cận dưới và cận trên, Python hiểu là **lấy toàn bộ các hàng**.
            
    - **Phần cột (`:-1`)**:
        
        - Dấu hai chấm ở đầu: Bắt đầu từ chỉ mục 0 (cột đầu tiên).
            
        - `-1`: Đại diện cho chỉ mục của cột cuối cùng.
            
        - **Quy tắc quan trọng trong Python**: Một phạm vi (range) sẽ bao gồm cận dưới nhưng **loại trừ cận trên**.
            
        - $\rightarrow$ Lệnh này sẽ lấy từ cột đầu tiên đến sát cột cuối cùng (loại bỏ cột biến phụ thuộc).
            
4. **`.values`**: Chuyển đổi dữ liệu từ định dạng Pandas DataFrame sang mảng NumPy (cần thiết cho các mô hình máy học).
    

## Lưu ý quan trọng

- Đoạn mã này là một "thủ thuật" (trick) có thể áp dụng cho hầu hết các bộ dữ liệu, bất kể số lượng cột là bao nhiêu.
    
- **Điều kiện áp dụng**: Bộ dữ liệu phải được sắp xếp sao cho các biến độc lập (features) nằm ở các cột đầu và biến phụ thuộc (dependent variable vector) nằm ở cột cuối cùng.
