## Thiết lập môi trường và Nhập dữ liệu cho SVR

## Chuẩn bị Notebook

- **Tạo bản sao:** Tạo một bản sao mới của file notebook gốc để thực hành lại từ đầu.
    
- **Làm sạch:** Xóa toàn bộ các ô chứa mã nguồn (code cells) cũ để tự viết lại.
    
- **Giữ cấu trúc:** Giữ lại các ô văn bản (text cells) để duy trì cấu trúc bài học.
    
- **Lưu ý:** Không xem trước kết quả cuối cùng để đảm bảo tính khách quan khi thực hành.
    

## Các bước khởi tạo (Data Preprocessing)

Giai đoạn tiền xử lý dữ liệu cơ bản được thực hiện nhanh chóng dựa trên các mẫu (template) đã có từ các bài trước:

1. **Nhập thư viện (Importing Libraries)**:  
    Sử dụng các thư viện chuẩn cho Data Science.
    
    python
    
    `import numpy as np import matplotlib.pyplot as plt import pandas as pd`
    
2. **Nhập tập dữ liệu (Importing the Dataset)**:  
    Sử dụng lại bộ dữ liệu lương (Position Salaries) giống như bài Hồi quy đa thức.
    
    python
    
    `dataset = pd.read_csv('Position_Salaries.csv') X = dataset.iloc[:, 1:-1].values y = dataset.iloc[:, -1].values`
    
3. **Tải dữ liệu lên môi trường (Upload Dataset)**:
    
    - Nếu dùng Google Colab, cần tải file `Position_Salaries.csv` lên.
        
    - Đường dẫn thư mục: `Part 2 - Regression` -> `Support Vector Regression` -> `Python`.
        

## Lưu ý quan trọng về Feature Scaling

- Trong bài này, quy trình tiền xử lý **dừng lại trước bước Quy chuẩn hóa dữ liệu (Feature Scaling)**.
    
- **Lý do**: Việc áp dụng Feature Scaling cho SVR có những đặc thù riêng và phức tạp hơn so với các mô hình trước, do đó sẽ được tách riêng thành một bài học chi tiết ngay sau bài này.
    
- **Yêu cầu**: Cần chuẩn bị kỹ lưỡng để xử lý bước này trong bài tiếp theo.