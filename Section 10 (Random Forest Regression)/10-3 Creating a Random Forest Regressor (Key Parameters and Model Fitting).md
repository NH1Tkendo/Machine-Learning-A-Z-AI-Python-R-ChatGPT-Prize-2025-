## Thực hành: Xây dựng và Huấn luyện mô hình

## 1. Khởi tạo và Huấn luyện (Training)

Không giống như _Cây quyết định (Decision Tree)_ chỉ cần tham số `random_state`, đối với _Rừng ngẫu nhiên (Random Forest)_, ta cần quan tâm đến một tham số quan trọng là số lượng cây.

- **Lớp sử dụng**: `RandomForestRegressor`
    
- **Tham số quan trọng**:
    
    - `n_estimators`: Số lượng cây (estimators) trong rừng. Trong bài thực hành này, ta thiết lập là **10**.
        
    - `random_state`: Thiết lập bằng `0` để cố định hạt giống ngẫu nhiên, đảm bảo kết quả thực hành giống nhau giữa các lần chạy.
        
- **Phương thức**: Sử dụng `.fit(X, y)` để huấn luyện trên toàn bộ tập dữ liệu.
    

python

`# Import lớp RandomForestRegressor (đã thực hiện ở bước trước) from sklearn.ensemble import RandomForestRegressor # Khởi tạo đối tượng regressor # n_estimators = 10: Sử dụng 10 cây quyết định # random_state = 0: Cố định kết quả ngẫu nhiên regressor = RandomForestRegressor(n_estimators=10, random_state=0) # Huấn luyện mô hình trên toàn bộ tập dữ liệu regressor.fit(X, y)`

## 2. Dự đoán kết quả (Prediction)

Sau khi huấn luyện, ta tiến hành dự đoán mức lương cho vị trí cấp bậc `6.5`.

- **Cú pháp**: Phương thức `.predict()` yêu cầu đầu vào là mảng 2 chiều (2D array), do đó cần sử dụng hai cặp ngoặc vuông `[[ ]]`.
    
- **Kết quả**: Mô hình dự đoán giá trị khoảng **167,000**.
    
- **Đánh giá**: Kết quả này rất sát với giá trị thực tế mà nhân viên đã đề cập (160k), cho thấy độ chính xác cao hơn so với các mô hình trước đó.
    

python

`# Dự đoán mức lương cho cấp bậc 6.5 regressor.predict([[6.5]])`

## 3. Trực quan hóa và Nhận xét (Visualization)

Khi vẽ biểu đồ kết quả của _Random Forest Regression_:

- **Hình dạng**: Biểu đồ vẫn có dạng bậc thang (step function) tương tự như _Decision Tree_.
    
- **Sự khác biệt**: Có nhiều bậc (steps) hơn. Thay vì một bậc cho mỗi cấp độ vị trí, _Random Forest_ tạo ra nhiều bước nhỏ giữa các khoảng.
    
- **Nguyên nhân**: Do mô hình tính trung bình cộng từ dự đoán của 10 cây (nhiều điểm chia - splits hơn), tạo ra nhiều mức giá trị dự đoán khác nhau.
    

## Lưu ý về dữ liệu

- Mô hình _Random Forest_ thường phát huy hiệu quả tốt nhất và phù hợp hơn với các bộ dữ liệu nhiều chiều (high dimensional datasets - nhiều features) hơn là bộ dữ liệu đơn giản 1 chiều như trong bài thực hành này.
    
- Nội dung tiếp theo của khóa học sẽ hướng dẫn cách chọn lựa mô hình tốt nhất (Model Selection) cho bất kỳ tập dữ liệu nào.