## Dự đoán kết quả mới với Decision Tree Regression

Sau khi huấn luyện mô hình, bước tiếp theo là dự đoán mức lương cho vị trí cấp độ `6.5`. Quá trình này đơn giản hơn so với mô hình SVR vì không yêu cầu bước xử lý dữ liệu phức tạp.

## 1. Cách thực hiện

Khác với SVR, Cây Hồi quy **không yêu cầu mở rộng tính năng (Feature Scaling)**. Do đó:

- Không cần sử dụng phương thức `transform`.
    
- Gọi trực tiếp phương thức `.predict()` từ đối tượng `regressor`.
    
- **Lưu ý định dạng**: Giá trị đầu vào phải được đặt trong **mảng 2 chiều (2D array)**, ký hiệu bằng cặp dấu ngoặc vuông kép `[[ ]]`.
    

## 2. Mã nguồn (Code)

python

`# Dự đoán mức lương cho vị trí cấp độ 6.5 # Input phải là mảng 2 chiều: [[6.5]] regressor.predict([[6.5]])`

## 3. Phân tích kết quả

- **Kết quả dự đoán**: Mô hình trả về giá trị là **$150,000**.
    
- **Đánh giá trong ngữ cảnh bài toán**:
    
    - Kết quả này thấp hơn mức lương mà nhân viên yêu cầu (khoảng $160,000+).
        
    - So với các mô hình trước, đây có thể được coi là một dự đoán chưa tối ưu trong tình huống cụ thể này.
        

## 4. Hạn chế của mô hình (Lý thuyết quan trọng)

Giảng viên nhấn mạnh một đặc điểm quan trọng về bản chất của Cây Hồi quy:

- **Không phù hợp cho dữ liệu ít chiều**: Cây Hồi quy không phải là lựa chọn tốt nhất cho các tập dữ liệu chỉ có **một biến đặc trưng (single feature dataset)**.
    
- **Thế mạnh thực sự**: Mô hình này được thiết kế và hoạt động hiệu quả hơn trên các tập dữ liệu nhiều chiều (high-dimensional datasets) với nhiều đặc trưng phức tạp.
    
- **Hệ quả**: Do đặc điểm này, biểu đồ trực quan hóa (sẽ thực hiện ở bài sau) của Cây Hồi quy trên dữ liệu 2D sẽ trông không "mượt mà" hoặc đẹp mắt như các mô hình hồi quy khác.