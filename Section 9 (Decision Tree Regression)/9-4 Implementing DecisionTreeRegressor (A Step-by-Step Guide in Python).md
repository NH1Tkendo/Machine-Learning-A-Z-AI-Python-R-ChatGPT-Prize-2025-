## 1. Tìm hiểu và Lựa chọn Class phù hợp

Khi làm việc với `Scikit-learn` để xây dựng mô hình cây quyết định, cần phân biệt rõ hai lớp:

- `DecisionTreeClassifier`: Dùng cho bài toán phân loại (dự đoán danh mục/nhãn).
    
- `DecisionTreeRegressor`: Dùng cho bài toán hồi quy (dự đoán giá trị số liên tục).
    

$\rightarrow$ Trong bài này, chúng ta sử dụng `DecisionTreeRegressor` để dự đoán mức lương (giá trị liên tục).

## 2. Các bước Xây dựng và Huấn luyện Mô hình

## Bước 1: Import thư viện

Sử dụng module `tree` từ thư viện `sklearn`.

python

`from sklearn.tree import DecisionTreeRegressor`

## Bước 2: Khởi tạo đối tượng (Instance)

Tạo biến `regressor` là một thể hiện của lớp `DecisionTreeRegressor`.

- **Tham số `random_state = 0`**:
    
    - Được sử dụng để cố định "hạt giống" ngẫu nhiên (seed).
        
    - Mục đích: Đảm bảo kết quả huấn luyện là nhất quán giữa các lần chạy và giống nhau giữa người hướng dẫn và học viên.
        
    - Các tham số khác có thể để mặc định. Việc tinh chỉnh tham số (parameter tuning) sẽ được học kỹ hơn ở phần 10 của khóa học.
        

python

`regressor = DecisionTreeRegressor(random_state = 0)`

## Bước 3: Huấn luyện mô hình (Training)

Sử dụng phương thức `.fit()` để huấn luyện mô hình trên toàn bộ tập dữ liệu.

- **Đầu vào**:
    
    - `X`: Ma trận các biến độc lập (Matrix of features - ở đây là cấp độ vị trí).
        
    - `y`: Vectơ biến phụ thuộc (Dependent variable vector - ở đây là mức lương).
        

python

`regressor.fit(X, y)`

## 3. Bài tập thực hành tiếp theo

- **Nhiệm vụ**: Sử dụng mô hình đã huấn luyện để dự đoán mức lương cho vị trí có cấp độ `6.5`.
    
- **Gợi ý**: Không có bẫy hay khó khăn nào, áp dụng tương tự các mô hình trước đó.
    

---

**Tổng kết:** Quy trình huấn luyện mô hình Cây Hồi quy rất đơn giản và tuân theo cấu trúc chuẩn của Scikit-learn: _Import Class_ $\rightarrow$ _Khởi tạo Object_ $\rightarrow$ _Fit dữ liệu_.