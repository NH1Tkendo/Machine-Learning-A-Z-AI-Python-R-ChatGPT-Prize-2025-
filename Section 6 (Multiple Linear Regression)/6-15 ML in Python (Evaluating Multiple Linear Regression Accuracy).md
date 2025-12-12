## Đánh giá Kết quả Dự đoán và Tổng kết

## Hoàn thiện Mã nguồn So sánh

Để hiển thị kết quả so sánh giữa lợi nhuận dự đoán và thực tế một cách trực quan nhất, chúng ta thực hiện ghép hai vectơ theo chiều ngang.

- **Mã nguồn hoàn chỉnh**:
    

python

`# In ra ma trận so sánh: [Lợi nhuận dự đoán, Lợi nhuận thực tế] print(np.concatenate((y_pred.reshape(len(y_pred),1), y_test.reshape(len(y_test),1)),1))`

- **Giải thích tham số `axis=1`**:
    
    - `0`: Ghép nối theo chiều dọc (chồng lên nhau).
        
    - `1`: Ghép nối theo chiều ngang (đặt cạnh nhau). Ở đây ta dùng `1` để tạo bảng so sánh 2 cột.
        

## Phân tích Kết quả Thực tế

Khi chạy mã nguồn trên, ta thu được bảng so sánh cho 10 startups trong tập kiểm tra (Test set).

- **Cột bên trái (`y_pred`)**: Lợi nhuận dự đoán.
    
- **Cột bên phải (`y_test`)**: Lợi nhuận thực tế.
    

**Nhận xét chi tiết từng trường hợp (ví dụ)**:

1. **Startup 1**: Dự đoán ~103,000 / Thực tế 103,200 $\rightarrow$ **Rất chính xác**.
    
2. **Startup 2**: Dự đoán ~132,500 / Thực tế 144,000 $\rightarrow$ Khá, nhưng có sai số.
    
3. **Startup 8**: Dự đoán ~98,000 / Thực tế 97,000 $\rightarrow$ **Rất tốt**.
    
4. **Startup 10**: Dự đoán ~167,000 / Thực tế 166,000 $\rightarrow$ **Tuyệt vời**.
    

$\rightarrow$ **Kết luận chung**:

- Mô hình Hồi quy Tuyến tính Đa biến hoạt động khá tốt trên tập dữ liệu này.
    
- Có những dự đoán rất sát thực tế, một số khác ở mức chấp nhận được.
    
- Điều này cho thấy tập dữ liệu có mối tương quan tuyến tính nhất định, mặc dù không hoàn hảo.
    

## Bài học về Hiệu suất và Tối ưu hóa

- **Về việc tinh chỉnh mô hình (Model Tuning)**:
    
    - Bạn có thể thử áp dụng _Backward Elimination_ để chọn lọc đặc trưng kỹ hơn.
        
    - Tuy nhiên, giảng viên lưu ý rằng với Hồi quy tuyến tính, việc này thường không cải thiện hiệu suất đáng kể so với việc dùng lớp `LinearRegression` mặc định (vốn đã tự động tối ưu hóa tốt).
        
    - **Lời khuyên**: Trong thực tế, thay vì mất quá nhiều thời gian tinh chỉnh một mô hình đơn lẻ, hãy thử nghiệm nhiều loại mô hình khác nhau (như Polynomial Regression, Random Forest...) và chọn ra mô hình có độ chính xác cao nhất (Model Selection).
        

## Hướng đi tiếp theo

- **Với người học Python**:
    
    - Bạn đã hoàn thành phần Hồi quy Tuyến tính Đa biến.
        
    - Bài học tiếp theo sẽ là **Hồi quy Đa thức (Polynomial Regression)**.
        
    - Đây là mô hình cần thiết để xử lý các tập dữ liệu có mối quan hệ **phi tuyến tính (non-linear)**, nơi mà hồi quy tuyến tính hoạt động kém hiệu quả.
        
- **Với người học R**:
    
    - Chuyển sang phần hướng dẫn thực hành bằng ngôn ngữ R.