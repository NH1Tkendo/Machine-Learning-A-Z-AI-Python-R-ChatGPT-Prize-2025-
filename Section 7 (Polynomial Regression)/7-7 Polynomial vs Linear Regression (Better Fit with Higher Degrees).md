## 1. Giải pháp cho phần Trực quan hóa Hồi quy Đa thức

Để vẽ đường cong dự đoán chính xác cho mô hình đa thức, chúng ta cần thay đổi tham số trong hàm `predict()`.

## Vấn đề

Mô hình `lin_reg_2` đã được huấn luyện trên ma trận đặc trưng biến đổi ($X_{poly}$), không phải trên ma trận $X$ ban đầu. Do đó, khi dự đoán, chúng ta cũng phải đưa vào dữ liệu đã được biến đổi tương ứng.

## Mã nguồn chính xác

Trong hàm `predict()`, thay vì truyền `X`, ta truyền `poly_reg.fit_transform(X)`.

python

`# Thay đổi tiêu đề plt.title('Truth or Bluff (Polynomial Regression)') # Vẽ đường dự đoán # Sử dụng lin_reg_2 để dự đoán # Dữ liệu đầu vào phải được biến đổi qua poly_reg.fit_transform(X) plt.plot(X, lin_reg_2.predict(poly_reg.fit_transform(X)), color = 'blue')`

## Kết quả (với bậc 2)

- Đường dự đoán là một đường cong (parabol).
    
- Độ khớp tốt hơn nhiều so với đường thẳng, đặc biệt ở các điểm dữ liệu mà mô hình tuyến tính sai lệch lớn.
    

---

## 2. Nâng cấp Mô hình: Tăng bậc Đa thức (Degree = 4)

Để mô hình khớp chặt chẽ hơn nữa với dữ liệu, ta tăng bậc của đa thức từ 2 lên 4.

## Phương trình mới

y=b0+b1x1+b2x12+b3x13+b4x14y = b_0 + b_1x_1 + b_2x_1^2 + b_3x_1^3 + b_4x_1^4y=b0+b1x1+b2x12+b3x13+b4x14

## Thực hiện

1. Quay lại cell khởi tạo `poly_reg`, đổi `degree = 2` thành `degree = 4`.
    
2. Chạy lại toàn bộ quá trình huấn luyện:
    
    - Tạo lại `X_poly` với bậc 4.
        
    - Huấn luyện lại `lin_reg_2`.
        
    - Chạy lại cell trực quan hóa.
        

## Kết quả (với bậc 4)

- Đường cong đi qua gần như tất cả các điểm dữ liệu thực tế.
    
- **Lưu ý:** Đây là hiện tượng **Overfitting** (Quá khớp), nhưng trong bài toán cụ thể này (cần dự đoán chính xác cho một trường hợp nội suy), điều này là chấp nhận được và mong muốn.
    

---

## 3. Làm mượt đường cong (Smoother Curve Visualization)

Mặc dù mô hình đã chính xác, nhưng biểu đồ mặc định nối các điểm dự đoán bằng các đoạn thẳng, tạo cảm giác gấp khúc. Để đường cong trông mượt mà hơn, ta cần tăng mật độ các điểm dữ liệu trên trục X.

## Kỹ thuật thực hiện

Thay vì chỉ dự đoán tại các điểm số nguyên (1, 2, 3...), ta tạo ra một dãy số liên tục với bước nhảy nhỏ (ví dụ: 0.1).

## Mã nguồn (Tham khảo)

python

`# Tạo mảng X_grid với độ phân giải cao (bước nhảy 0.1) # np.arange(start, stop, step) X_grid = np.arange(min(X), max(X), 0.1)  # Reshape để đưa về dạng ma trận cột (n_samples, 1) đúng chuẩn input của model X_grid = X_grid.reshape((len(X_grid), 1)) # Vẽ biểu đồ với X_grid plt.scatter(X, y, color = 'red') plt.plot(X_grid, lin_reg_2.predict(poly_reg.fit_transform(X_grid)), color = 'blue') plt.title('Truth or Bluff (Polynomial Regression)') plt.xlabel('Position level') plt.ylabel('Salary') plt.show()`

## Ý nghĩa

Bước này chủ yếu phục vụ mục đích trình bày (presentation) để biểu đồ đẹp và chuyên nghiệp hơn, giúp người xem dễ hình dung mối quan hệ phi tuyến tính liên tục của mô hình. Trong thực tế với nhiều biến (features), ta hiếm khi thực hiện bước này vì không thể vẽ biểu đồ quá nhiều chiều.