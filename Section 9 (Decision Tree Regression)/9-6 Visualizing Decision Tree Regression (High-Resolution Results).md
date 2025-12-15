## Trực quan hóa Cây Hồi quy (Visualizing Decision Tree Regression)

Bước cuối cùng là trực quan hóa kết quả của mô hình Cây Hồi quy ở **độ phân giải cao (High Resolution)**. Chúng ta sẽ tái sử dụng và điều chỉnh mã nguồn từ bài Hồi quy đa thức (Polynomial Regression).

## Cách thực hiện (Coding)

Việc thực hiện đơn giản hơn so với các mô hình trước (như SVR hay Polynomial) vì Cây Hồi quy không yêu cầu mở rộng tính năng (Feature Scaling) hay biến đổi đa thức.

**Các thay đổi cần thiết trong mã nguồn:**

1. **Tiêu đề:** Đổi thành "Decision Tree Regression".
    
2. **Dự đoán:** Thay thế đoạn mã biến đổi `poly_reg.fit_transform(X_grid)` bằng việc gọi trực tiếp `regressor.predict(X_grid)`.
    

**Đoạn mã mẫu:**

python

`# Trực quan hóa kết quả Decision Tree Regression (Độ phân giải cao) X_grid = np.arange(min(X), max(X), 0.1) # Tạo lưới dữ liệu dày hơn (bước nhảy 0.1) X_grid = X_grid.reshape((len(X_grid), 1)) # Reshape thành mảng 2 chiều plt.scatter(X, y, color = 'red') # Điểm dữ liệu thực tế plt.plot(X_grid, regressor.predict(X_grid), color = 'blue') # Đường dự đoán plt.title('Truth or Bluff (Decision Tree Regression)') plt.xlabel('Position level') plt.ylabel('Salary') plt.show()`

## Phân tích kết quả biểu đồ

Khi chạy đoạn mã trên, biểu đồ thu được sẽ có hình dạng đặc biệt, không phải là một đường cong mượt mà:

- **Hình dạng bậc thang (Stair-looking curve):** Đường hồi quy trông giống như các bậc thang.
    
- **Nguyên lý hoạt động:**
    
    - Mô hình chia dữ liệu thành các khoảng (intervals) thông qua các nút (nodes).
        
    - Trong một khoảng nhất định (ví dụ: từ vị trí $5.5$ đến $6.5$), mô hình dự đoán cùng một mức lương (giá trị trung bình của lá đó).
        
    - Do đó, đường dự đoán là các đoạn thẳng nằm ngang nối tiếp nhau.
        
- **Tính không liên tục:** Đường hồi quy không liên tục mà có các bước nhảy thẳng đứng (vertical jumps) giữa các cấp độ vị trí.
    

## Kết luận về mô hình

1. **Đối với dữ liệu 2D (1 biến độc lập):**
    
    - Mô hình Cây Hồi quy **không phù hợp** để trực quan hóa hoặc giải quyết các bài toán đơn giản ít chiều.
        
    - Kết quả hiển thị (đường bậc thang) trông thô sơ và thiếu tính thẩm mỹ so với các mô hình đường cong liên tục.
        
2. **Đối với dữ liệu nhiều chiều (High-dimensional datasets):**
    
    - Đây mới là thế mạnh thực sự của Cây Hồi quy.
        
    - Mô hình hoạt động rất hiệu quả và mạnh mẽ khi xử lý các tập dữ liệu phức tạp với nhiều đặc trưng (features).
        

---

**Tổng kết phần học:** Bạn đã hoàn thành việc xây dựng, huấn luyện và trực quan hóa mô hình Cây Hồi quy. Mô hình tiếp theo và cũng là mô hình cuối cùng trong phần Hồi quy sẽ là **Rừng ngẫu nhiên (Random Forest Regression)**.