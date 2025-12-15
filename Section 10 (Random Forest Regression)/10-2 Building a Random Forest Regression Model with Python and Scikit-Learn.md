## Thực hành Xây dựng Hồi quy Rừng ngẫu nhiên (Random Forest Regression)

## Tổng quan

Đây là mô hình cuối cùng trong phần học về Hồi quy (Regression). Sau bài học này, khóa học sẽ chuyển sang phần đánh giá và lựa chọn mô hình tối ưu cho tập dữ liệu thực tế.

Mô hình Hồi quy Rừng ngẫu nhiên có cấu trúc mã nguồn rất giống với **Hồi quy Cây quyết định (Decision Tree Regression)**. Do đó, quy trình thực hiện sẽ tận dụng lại code cũ và chỉ thay đổi phần huấn luyện mô hình.

## Chuẩn bị môi trường

1. Truy cập thư mục tài liệu: `Part 2 - Regression` → `Random Forest Regression`.
    
2. Mở tệp `random_forest_regression.ipynb`.
    
3. Công cụ sử dụng: Google Colaboratory hoặc Jupyter Notebook.
    

## Cấu trúc mã nguồn

Quy trình thực hiện bao gồm các bước tương tự như Decision Tree:

- **Nhập thư viện (Import libraries)**: Giữ nguyên.
    
- **Nhập bộ dữ liệu (Import dataset)**: Sử dụng bộ dữ liệu `Position_Salaries.csv` (giữ nguyên).
    
- **Huấn luyện mô hình (Training)**: **Đây là phần duy nhất cần viết lại code mới.**
    
- **Dự đoán kết quả (Prediction)**: Cú pháp giữ nguyên.
    
- **Trực quan hóa (Visualization)**: Code vẽ biểu đồ giữ nguyên.
    

## Cách tìm và nhập thư viện Scikit-learn

Để sử dụng đúng lớp cho Random Forest Regression, ta có thể tra cứu trên tài liệu của Scikit-learn:

1. **Tìm kiếm**: Từ khóa `scikit-learn random forest regression`.
    
2. **Kết quả**:
    
    - Thư viện gốc: `sklearn`
        
    - Mô-đun chứa lớp: `ensemble` (Mô-đun học kết hợp)
        
    - Tên lớp: `RandomForestRegressor`
        

## Mã nguồn thực hiện (Python)

Bước đầu tiên để xây dựng mô hình là nhập lớp `RandomForestRegressor` từ thư viện `sklearn`.

python

`# Nhập lớp RandomForestRegressor từ mô-đun ensemble của thư viện scikit-learn from sklearn.ensemble import RandomForestRegressor # Các bước tiếp theo (khởi tạo và huấn luyện) sẽ được thực hiện trong bài sau`

> **Ghi chú**: Kỹ năng tra cứu tài liệu (documentation) rất quan trọng. Khi không nhớ tên lớp hoặc mô-đun, hãy tìm kiếm trực tiếp trên Google để lấy đường dẫn nhập (import path) chính xác.