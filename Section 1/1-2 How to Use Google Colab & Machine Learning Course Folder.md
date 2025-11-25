## Giới thiệu Môi trường Thực hành và Google Colab

Bài học này hướng dẫn cách tiếp cận tài nguyên khóa học và thiết lập môi trường lập trình Python thông qua Google Colab.

## Tài nguyên Khóa học (Course Resources)

Toàn bộ tài liệu được tập hợp trong thư mục **Machine Learning A to Z codes and dataset**, bao gồm:

- **Slides và tài liệu tham khảo:** Dùng để ôn tập lý thuyết.
    
- **Mã nguồn (Source Code):** Có sẵn cho cả hai ngôn ngữ Python và R.
    
- **Tập dữ liệu (Datasets):** Các file dữ liệu dùng để huấn luyện mô hình.
    
- **Hình ảnh thân thiện với người mù màu:** Dùng cho việc trực quan hóa dữ liệu.
    

**Cấu trúc thư mục mã nguồn Python:**  
Mỗi bài học (ví dụ: _Part 3 - Classification / Logistic Regression_) sẽ cung cấp 2 định dạng file:

- `.ipynb`: Dành cho **Google Colab** hoặc **Jupyter Notebook**.
    
- `.py`: Dành cho các IDE truyền thống như **Spyder** hoặc **Anaconda**.
    

## Tại sao chọn Google Colab?

Giảng viên khuyến nghị sử dụng **Google Colab** cho người mới bắt đầu vì các ưu điểm sau:

- **Giao diện thân thiện (User-friendly):** Dễ sử dụng, không cần cấu hình phức tạp.
    
- **Môi trường cài đặt sẵn (Pre-installed environment):** Các thư viện phổ biến cho khoa học dữ liệu và học máy đã được cài đặt sẵn, không cần thao tác cài đặt thủ công qua terminal.
    
    - Ví dụ: `TensorFlow` (cho Học sâu - Deep Learning), `XGBoost`, `LightGBM`.
        

## Hướng dẫn thao tác trên Google Colab

## 1. Mở và Sao chép Notebook

Khi mở file `.ipynb` từ thư mục tài nguyên được chia sẻ, file sẽ ở chế độ **Chỉ đọc (Read-only)** để đảm bảo tính toàn vẹn của dữ liệu gốc. Để chỉnh sửa và chạy code, bạn cần tạo bản sao cá nhân:

1. Vào menu **Tệp (File)**.
    
2. Chọn **Lưu bản sao vào Drive (Save a copy in Drive)**.
    
3. File bản sao sẽ được lưu trong thư mục _Colab Notebooks_ trên Google Drive của bạn và cho phép chỉnh sửa thoải mái.
    

## 2. Tải dữ liệu lên (Importing Datasets)

Để mô hình có thể đọc được dữ liệu:

1. Nhấn vào biểu tượng **Thư mục (Folder)** ở thanh bên trái.
    
2. Nhấn nút **Tải lên (Upload)**.
    
3. Chọn file `.csv` tương ứng từ máy tính (ví dụ: `social_network_ads.csv`).
    

## 3. Chạy chương trình (Executing Code)

- Để chạy toàn bộ code trong notebook: Chọn **Thời gian chạy (Runtime)** $\to$ **Chạy tất cả (Run all)**.
    
- Hệ thống sẽ thực thi từng ô lệnh (cell), huấn luyện mô hình và hiển thị kết quả trực quan hóa (ví dụ: biểu đồ vùng dự đoán của Hồi quy Logistic).
    

## Kiểm tra thư viện cài đặt sẵn

Bạn có thể kiểm tra tính tiện dụng của Google Colab bằng cách thử nhập các thư viện mạnh mẽ mà không cần cài đặt trước:

python

`# Không cần chạy lệnh pip install import tensorflow import xgboost # Kết quả: Các cell chạy thành công mà không báo lỗi thiếu thư viện`