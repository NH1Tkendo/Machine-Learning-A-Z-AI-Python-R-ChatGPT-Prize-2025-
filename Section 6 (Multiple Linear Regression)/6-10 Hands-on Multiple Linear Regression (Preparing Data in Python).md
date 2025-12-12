## Thực hành: Tiền xử lý dữ liệu cho Hồi quy tuyến tính đa biến

## 1. Sử dụng Template có sẵn

Để tối ưu hóa thời gian, chúng ta tái sử dụng các đoạn mã từ _template tiền xử lý dữ liệu_ đã học ở phần trước. Các bước thực hiện:

- **Nhập thư viện**: Copy & paste đoạn mã import các thư viện cần thiết.
    
- **Nhập tập dữ liệu**: Copy & paste đoạn mã import dataset.
    
- **Chia tập dữ liệu**: Copy & paste đoạn mã chia dữ liệu thành _Training set_ và _Test set_.
    

## 2. Điều chỉnh mã nguồn cho phù hợp với Dataset mới

Chỉ cần thay đổi tên file dữ liệu trong đoạn mã nhập dataset:

- Tên cũ: `Data.csv` (ví dụ)
    
- Tên mới: `50_Startups.csv`
    

Các dòng lệnh chọn cột không cần thay đổi vì cấu trúc vẫn tuân theo quy tắc chung:

- `X` (biến độc lập): Lấy tất cả các cột trừ cột cuối cùng.
    
- `y` (biến phụ thuộc): Chỉ lấy cột cuối cùng (Profit).
    

## 3. Mã hóa dữ liệu phân loại (Encoding Categorical Data)

Đây là bước quan trọng nhất cần tùy biến.

- **Công cụ**: Sử dụng kỹ thuật **One-Hot Encoding** (đã có trong bộ công cụ tiền xử lý).
    
- **Vị trí cần sửa đổi**: Chỉ số cột (column index) cần mã hóa.
    
    - Trong dataset cũ: Biến phân loại nằm ở cột đầu tiên (index = 0).
        
    - Trong dataset `50_Startups`: Biến phân loại (`State`) nằm ở cột thứ 4.
        
    - **Lưu ý quan trọng**: Python bắt đầu đếm từ 0.
        
        - R&D Spend: Index 0
            
        - Administration: Index 1
            
        - Marketing Spend: Index 2
            
        - **State: Index 3**
            
    - $\rightarrow$ Cần thay đổi index trong hàm `ColumnTransformer` thành **3**.
        

## 4. Tải dữ liệu và Kiểm tra

- **Upload Dataset**: Tải file `50_Startups.csv` lên môi trường Google Colab/Jupyter Notebook.
    
- **Chạy và Kiểm tra**: Thực thi từng ô mã (cell) và nên thêm các lệnh `print` để kiểm tra trực quan các biến `X`, `y` sau mỗi bước xử lý, đảm bảo dữ liệu được biến đổi chính xác (đặc biệt là sau khi One-Hot Encoding).