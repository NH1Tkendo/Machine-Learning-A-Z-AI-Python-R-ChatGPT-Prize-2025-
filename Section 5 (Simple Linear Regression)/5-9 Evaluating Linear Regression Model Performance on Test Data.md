## Trực quan hóa kết quả trên Tập kiểm tra (Visualizing Test Set Results)

Sau khi đánh giá trên tập huấn luyện, bước quan trọng tiếp theo là kiểm chứng hiệu quả của mô hình trên các dữ liệu mới mà nó chưa từng được "học" (tập kiểm tra).

## Mã nguồn thực hiện

Chúng ta sử dụng lại cấu trúc mã nguồn của bước trước, nhưng cần thực hiện một số thay đổi nhỏ để hiển thị dữ liệu kiểm tra.

**Các thay đổi cần thiết:**

1. **Dữ liệu điểm (Scatter plot)**: Thay `X_train`, `y_train` bằng **`X_test`, `y_test`**. Điều này giúp hiển thị các điểm dữ liệu thực tế của nhân viên trong tập kiểm tra.
    
2. **Đường hồi quy (Regression line)**:
    
    - Trong hàm `plt.plot`, ta **giữ nguyên** `X_train` và `regressor.predict(X_train)`.
        
    - **Lý do**: Đường hồi quy được tạo ra từ một phương trình duy nhất (unique equation) sau khi huấn luyện. Việc vẽ đường thẳng này dựa trên tập _train_ hay _test_ đều cho ra cùng một hình ảnh hình học. Tuy nhiên, giữ nguyên `X_train` giúp đường thẳng bao phủ phạm vi dữ liệu rộng hơn (do tập train lớn hơn).
        
3. **Tiêu đề và Nhãn**: Cập nhật tiêu đề biểu đồ thành "Test set".
    

python

`# Trực quan hóa kết quả trên tập kiểm tra (Test set) plt.scatter(X_test, y_test, color = 'red') # Hiển thị điểm dữ liệu thực tế của tập test plt.plot(X_train, regressor.predict(X_train), color = 'blue') # Đường hồi quy (giữ nguyên) plt.title('Salary vs Experience (Test set)') plt.xlabel('Years of Experience') plt.ylabel('Salary') plt.show()`

## Phân tích biểu đồ

- **Quan sát**: Các điểm màu đỏ (dữ liệu thực tế của tập test) nằm rất gần đường màu xanh (dự đoán của mô hình).
    
- **Kết luận**:
    
    - Mô hình đã thực hiện tốt việc dự đoán trên các quan sát mới.
        
    - Không có hiện tượng quá khớp (overfitting) hoặc sai lệch lớn.
        

## Lưu ý quan trọng về tính chất dữ liệu

Mặc dù kết quả rất tốt, cần hiểu rõ lý do đằng sau:

- **Nguyên nhân thành công**: Bộ dữ liệu này có **mối quan hệ tuyến tính hoàn hảo (linear relationship)** hoặc tương quan tuyến tính (linear correlations) giữa số năm kinh nghiệm và mức lương.
    
- **Thực tế**: Nhiều bộ dữ liệu đời thực sẽ có mối quan hệ phi tuyến tính (non-linear). Khi đó, mô hình _Hồi quy tuyến tính đơn giản_ sẽ không hiệu quả và ta cần dùng các mô hình phức tạp hơn (sẽ học sau) như:
    
    - Hồi quy đa thức (Polynomial Regression)
        
    - Hồi quy Vector hỗ trợ (SVR)
        

## Tổng kết và bước tiếp theo

Chúng ta đã hoàn thành mô hình máy học đầu tiên: **Hồi quy tuyến tính đơn giản (Simple Linear Regression)** – sử dụng **01** biến độc lập để dự đoán kết quả.

**Chủ đề tiếp theo:**

- **Hồi quy tuyến tính đa biến (Multiple Linear Regression)**: Mở rộng bài toán khi có **nhiều** biến độc lập (multiple features) tham gia vào việc dự đoán, thay vì chỉ một.