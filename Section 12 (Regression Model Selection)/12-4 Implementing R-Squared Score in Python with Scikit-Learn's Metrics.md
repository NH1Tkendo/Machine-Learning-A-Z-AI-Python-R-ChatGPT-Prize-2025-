## Tra cứu API Scikit-Learn và Chỉ số R-Squared

## Cách tiếp cận tài liệu Scikit-Learn

- **API Reference**: Là nơi chứa toàn bộ thư viện, bao gồm các mô-đun `(modules)`, hàm `(functions)` và lớp `(classes)` của Scikit-Learn.
    
- **Mô-đun Metrics**: Để đánh giá mô hình, cần tìm đến mô-đun `sklearn.metrics`.
    
    - Mô-đun này chứa các chỉ số đo lường cho cả mô hình phân loại `(classification models)` và mô hình hồi quy `(regression models)`.
        

## Các chỉ số đánh giá mô hình hồi quy (Regression Metrics)

Trong danh sách các chỉ số hồi quy, có nhiều lựa chọn như:

- Sai số tuyệt đối trung bình `(mean absolute error)`
    
- Sai số bình phương trung bình `(mean squared error)`
    
- **Điểm R-squared** `(R-squared score)` hay còn gọi là hệ số xác định `(coefficient of determination)`.
    

> **Lưu ý**: Scikit-Learn không có sẵn hàm cho _Adjusted R-squared_, nhưng chỉ số **R-squared** cơ bản là đủ để đánh giá và so sánh hiệu suất giữa các mô hình hồi quy nhằm chọn ra mô hình tốt nhất.

## Triển khai Mã nguồn (Python)

Dựa trên tài liệu hướng dẫn và các ví dụ `(examples)` từ Scikit-Learn, quy trình thực hiện như sau:

1. **Import thư viện**: Lấy hàm `r2_score` từ mô-đun `metrics`.
    
2. **Gọi hàm**: So sánh vector kết quả thực tế `(y_test)` với vector dự đoán `(y_pred)`.
    

python

`# Import hàm r2_score từ thư viện from sklearn.metrics import r2_score # Tính toán hệ số R-squared # y_test: Các giá trị thực tế của biến phụ thuộc trong tập kiểm tra # y_pred: Các giá trị dự đoán cho cùng các quan sát đó r2_score(y_test, y_pred)`

## Kỹ năng học tập

- Việc tra cứu tài liệu gốc `(documentation)` là kỹ năng quan trọng.
    
- Khi không nhớ cách triển khai một chỉ số (như $R^2$), hãy tìm trong API, xem phần ví dụ và áp dụng đoạn mã mẫu vào bài toán thực tế.