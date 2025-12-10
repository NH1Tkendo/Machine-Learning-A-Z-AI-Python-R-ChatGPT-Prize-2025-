Dưới đây là ghi chú học tập về bước nhập thư viện trong quy trình tiền xử lý dữ liệu:

## Nhập thư viện (Importing Libraries)

## Mục đích

Đây là bước đầu tiên trong mọi mô hình học máy. Thư viện (Library) là tập hợp các mô-đun chứa các hàm và lớp, giúp thực hiện các tác vụ tính toán và xử lý dữ liệu mà không cần viết lại mã từ đầu.

## Các thư viện cốt lõi

Có 3 thư viện Python cơ bản cần nhập để phục vụ cho khoa học dữ liệu:

- **NumPy**:
    
    - **Chức năng**: Cho phép làm việc với các mảng (arrays).
        
    - **Lý do sử dụng**: Các mô hình học máy thường yêu cầu dữ liệu đầu vào dưới dạng mảng.
        
    - **Tên viết tắt**: `np`.
        
- **Matplotlib** (cụ thể là mô-đun `pyplot`):
    
    - **Chức năng**: Vẽ biểu đồ và đồ thị trực quan.
        
    - **Lý do sử dụng**: Hỗ trợ trực quan hóa dữ liệu và kết quả huấn luyện.
        
    - **Tên viết tắt**: `plt`.
        
- **Pandas**:
    
    - **Chức năng**: Nhập và xử lý bộ dữ liệu.
        
    - **Lý do sử dụng**: Giúp tạo ma trận đặc trưng (matrix of features) và vectơ biến phụ thuộc (dependent variable vector).
        
    - **Tên viết tắt**: `pd`.
        

## Mã nguồn (Source Code)

Cú pháp tiêu chuẩn: `import [tên_thư_viện] as [tên_viết_tắt]`

python

`import numpy as np import matplotlib.pyplot as plt import pandas as pd`