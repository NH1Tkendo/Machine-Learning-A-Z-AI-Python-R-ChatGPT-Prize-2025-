## Dự đoán Kết quả mới với SVR

Để dự đoán mức lương cho vị trí cấp độ 6.5, quy trình thực hiện phức tạp hơn so với các mô hình trước do phải xử lý **Feature Scaling** hai chiều (Input và Output).

## 1. Nguyên tắc Dự đoán

- Mô hình SVR đã được huấn luyện trên dữ liệu **đã quy chuẩn (scaled data)**.
    
- Do đó:
    
    - **Đầu vào (Input)** cho hàm `predict` phải là giá trị đã được quy chuẩn hóa.
        
    - **Đầu ra (Output)** từ hàm `predict` sẽ là giá trị đã được quy chuẩn hóa.
        
    - Cần thực hiện **nghịch đảo quy chuẩn (inverse transform)** cho đầu ra để lấy được giá trị thực tế (USD).
        

## 2. Quy trình và Mã nguồn

Các bước lồng ghép nhau trong một dòng lệnh như sau:

1. **Chuẩn bị Input (Level 6.5)**:
    
    - Đưa giá trị 6.5 vào mảng 2 chiều: `[[6.5]]`.
        
    - Quy chuẩn hóa Input bằng `sc_X`: `sc_X.transform([[6.5]])`.
        
2. **Thực hiện Dự đoán**:
    
    - Gọi hàm `predict` trên Input đã quy chuẩn: `regressor.predict(...)`.
        
    - Kết quả trả về là một giá trị lương _đã quy chuẩn_.
        
3. **Xử lý định dạng Output**:
    
    - Để tránh lỗi định dạng (format error) với hàm inverse transform, cần reshape kết quả dự đoán: `.reshape(-1, 1)`.
        
4. **Nghịch đảo quy chuẩn Output**:
    
    - Dùng `sc_y` để chuyển đổi ngược về giá trị gốc: `sc_y.inverse_transform(...)`.
        

**Mã nguồn tổng hợp:**

python

`# Dự đoán mức lương cho Level 6.5 # sc_X: Scaler của X (Position Level) # sc_y: Scaler của y (Salary) # regressor: Mô hình SVR đã train predicted_salary_scaled = regressor.predict(sc_X.transform([[6.5]])) predicted_salary = sc_y.inverse_transform(predicted_salary_scaled.reshape(-1, 1)) print(predicted_salary)`

## 3. Kết quả

- **Giá trị dự đoán**: Khoảng **170,370 USD**.
    
- **Nhận xét**: Kết quả này khá gần với mức kỳ vọng (160k) và hợp lý hơn so với Hồi quy tuyến tính. Mức độ chính xác sẽ được kiểm chứng rõ hơn khi vẽ biểu đồ trực quan hóa ở bài sau.