## Giới thiệu & Chuẩn bị môi trường

Trong phần này, chúng ta sẽ xây dựng mô hình Cây Hồi quy (Decision Tree Regression). Một ưu điểm lớn của mô hình này so với SVR là **không cần thực hiện Feature Scaling** (mở rộng tính năng).

## Tập dữ liệu & Công cụ

- **Thư mục làm việc**: `Part 2 Regression` > `Section 8 - Decision Tree Regression`.
    
- **File cần thiết**:
    
    - `decision_tree_regression.ipynb`: File notebook chứa mã nguồn (mở bằng Google Colab hoặc Jupyter Notebook).
        
    - `Position_Salaries.csv`: Tập dữ liệu quen thuộc về mức lương theo vị trí (từ cấp 1 đến 10, lương từ 45k đến 1 triệu USD).
        
- **Mục tiêu**: Huấn luyện mô hình để hiểu mối tương quan giữa _Position Level_ (Cấp độ vị trí) và _Salary_ (Mức lương).
    

## Lưu ý quan trọng về mô hình

- **Đặc điểm**: Mô hình Cây Hồi quy thực sự không hoạt động tốt nhất trên các tập dữ liệu quá đơn giản (chỉ có 1 biến đặc trưng) như tập _Position Salaries_. Kết quả trực quan hóa (visualization) có thể sẽ không đẹp.
    
- **Khả năng mở rộng**: Mã nguồn (code) được triển khai trong bài này **hoàn toàn có thể áp dụng** cho các tập dữ liệu phức tạp hơn với hàng trăm biến đặc trưng (features).
    
- **Yêu cầu tiền xử lý**:
    
    - Với dữ liệu phức tạp: Cần xử lý dữ liệu phân loại (categorical data) hoặc dữ liệu bị thiếu (missing data) nếu có.
        
    - **Feature Scaling**: KHÔNG cần thiết cho Cây Hồi quy (Decision Tree) và Rừng ngẫu nhiên (Random Forest).
        

## Quy trình triển khai (Coding)

## 1. Khởi tạo Notebook

- Mở file `.ipynb` trong Google Colab hoặc Jupyter Notebook.
    
- Tạo bản sao (Save a copy in Drive) để có thể chỉnh sửa code.
    
- **Giữ lại các bước cơ bản**: Do đây là lần thứ 3 làm việc với tập dữ liệu này, ta sẽ không viết lại từ đầu các bước nhập thư viện và nhập dữ liệu.
    
    - Importing the libraries (Nhập thư viện).
        
    - Importing the dataset (Nhập tập dữ liệu).
        

## 2. Các bước sẽ thực hiện lại

Chúng ta sẽ xóa và viết lại code cho các phần sau để nắm vững kỹ thuật:

1. **Training the model**: Huấn luyện mô hình Decision Tree Regression trên toàn bộ tập dữ liệu.
    
2. **Predicting**: Dự đoán kết quả mới.
    
3. **Visualization**: Trực quan hóa kết quả.
    

## 3. Lưu ý về Trực quan hóa (Visualization)

- Chỉ thực hiện trực quan hóa ở **độ phân giải cao (High Resolution)**.
    
- Lý do: Kết quả trực quan hóa ở độ phân giải thấp (Low Resolution) của mô hình Cây Hồi quy sẽ hiển thị không chính xác và không có ý nghĩa (sẽ được giải thích chi tiết ở cuối bài học).
    

---

**Ghi chú**: Hãy đảm bảo bạn đã sẵn sàng file `Position_Salaries.csv` và môi trường Python để bắt đầu viết code trong bài tiếp theo.