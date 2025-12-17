## Giới thiệu Dữ liệu và Quy trình Demo

## Bộ dữ liệu minh họa: Nhà máy điện chu trình hỗn hợp

Bộ dữ liệu được sử dụng để thực hành là **Combined Cycle Power Plant** (Nhà máy điện chu trình hỗn hợp), được lấy từ kho dữ liệu học máy UCI (UCI Machine Learning Repository).

- **Mục tiêu**: Dự đoán biến phụ thuộc là **sản lượng năng lượng** (energy output).
    
- **Các đặc trưng (Features)**: Gồm 4 yếu tố đầu vào dùng để dự đoán:
    
    1. Nhiệt độ môi trường (Ambient Temperature).
        
    2. Độ chân không khí thải (Exhaust Vacuum).
        
    3. Áp suất môi trường (Ambient Pressure).
        
    4. Độ ẩm tương đối (Relative Humidity).
        

> **Lưu ý**: Người học không cần hiểu về vật lý hay cơ chế hoạt động của nhà máy điện, chỉ cần xác định rõ đâu là các biến đầu vào (features) và đâu là biến mục tiêu cần dự đoán (dependent variable).

## Yêu cầu về cấu trúc dữ liệu

Để sử dụng bộ công cụ (toolkit) hiệu quả, dữ liệu cần đảm bảo các điều kiện sau:

- **Định dạng**: File `.csv`.
    
- **Cấu trúc cột**:
    
    - Các cột đầu tiên chứa các đặc trưng (features).
        
    - Cột cuối cùng chứa biến phụ thuộc (dependent variable).
        
- **Chất lượng dữ liệu**:
    
    - Không có dữ liệu bị thiếu (missing data).
        
    - Không có dữ liệu dạng phân loại (categorical data/strings).
        
    - _Ghi chú_: Nếu dữ liệu thực tế có chứa các vấn đề trên, cần sử dụng bộ công cụ tiền xử lý dữ liệu (Data Pre-processing toolkit) để xử lý trước khi đưa vào mô hình.
        

## Quy trình Demo và Thiết lập môi trường

Để bắt đầu thực hành và lựa chọn mô hình tốt nhất, quy trình thực hiện như sau:

1. **Sao chép mã nguồn (Make a copy)**:
    
    - Các file gốc thường ở chế độ "chỉ xem" (read-only).
        
    - Cần tạo bản sao lưu vào Google Drive cá nhân để có thể chỉnh sửa.
        
    - Thực hiện thao tác này cho cả 5 mô hình: Hồi quy tuyến tính bội, Đa thức, SVR, Cây quyết định, và Rừng ngẫu nhiên.
        
2. **Mở các file Notebook**:
    
    - Sử dụng Google Colab, Jupyter Notebook hoặc Spyder (Anaconda).
        
    - Mở lần lượt các file theo thứ tự đã học để dễ theo dõi.
        
3. **Cấu trúc mã nguồn chung (Generic Code Templates)**:  
    Các mẫu code được thiết kế tổng quát hóa cao độ, bao gồm các bước:
    
    - **Nhập thư viện (Importing libraries)**.
        
    - **Nhập dữ liệu (Importing the dataset)**:
        
        - Đây là phần duy nhất cần chỉnh sửa thủ công.
            
        - Chỉ cần thay đổi tên file `.csv` tại dòng lệnh: `Enter the name of your data set here`.
            
        - Code tự động chọn các cột đặc trưng ($X$) và cột biến phụ thuộc ($y$).
            
    - **Chia tập dữ liệu (Splitting the dataset)**:
        
        - Chia thành tập huấn luyện (training set) và tập kiểm tra (test set).
            
        - Bước này bắt buộc để có thể so sánh hiệu suất giữa các mô hình.
            
    - **Huấn luyện mô hình (Training)**: Áp dụng trên tập huấn luyện.
        
    - **Dự đoán (Predicting)**: Chạy trên tập kiểm tra.
        
    - **Đánh giá hiệu suất (Evaluating)**: Sử dụng hệ số $R^2$ (R-squared) để đo lường và so sánh kết quả.