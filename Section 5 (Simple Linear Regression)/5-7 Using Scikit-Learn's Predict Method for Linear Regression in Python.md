## Dự đoán kết quả trên tập kiểm tra (Predicting Test Set Results)

Sau khi mô hình đã được huấn luyện trên tập huấn luyện (Training set), bước tiếp theo là kiểm tra khả năng dự báo của mô hình trên tập kiểm tra (Test set).

## Nguyên lý thực hiện

- **Dữ liệu đầu vào**: Tập kiểm tra (`X_test`) chiếm 20% tổng dữ liệu (tương ứng với 6 quan sát/nhân viên). Dữ liệu này chỉ chứa thông tin về số năm kinh nghiệm.
    
- **Mục tiêu**: Sử dụng mô hình để dự đoán mức lương cho 6 nhân viên này.
    
- **Cơ chế đánh giá**: Kết quả dự đoán sẽ được so sánh với dữ liệu thực tế (`y_test` - còn gọi là _ground truth_) để xem độ lệch giữa dự báo và thực tế.
    

## Phân biệt các biến quan trọng

- **`y_test`**: Chứa mức lương **thực tế** của nhân viên (Dữ liệu gốc).
    
- **`y_pred`**: Chứa mức lương **dự đoán** do mô hình sinh ra.
    

## Triển khai Mã nguồn (Python)

Để thực hiện dự đoán, ta sử dụng phương thức `predict` từ thư viện Scikit-learn.

python

`# Dự đoán kết quả trên tập kiểm tra y_pred = regressor.predict(X_test)`

**Giải thích mã nguồn:**

- `regressor`: Đối tượng mô hình Hồi quy tuyến tính đã được huấn luyện (bằng hàm `fit` trước đó).
    
- `.predict()`: Phương thức dùng để dự báo giá trị cho các quan sát mới.
    
- `X_test`: Tham số đầu vào cho hàm dự đoán. Lưu ý chỉ truyền vào các đặc trưng (features) - ở đây là số năm kinh nghiệm, không truyền `y_test`.
    
- `y_pred`: Biến vectơ được tạo ra để lưu trữ các giá trị lương dự đoán tương ứng với `X_test`.