## Hồi quy tuyến tính đơn giản (Simple Linear Regression)

## Phương trình cơ bản

Phương trình tổng quát của hồi quy tuyến tính đơn giản được biểu diễn như sau:
![[SLR_Equation.png]]
y=b0+b1x1y = b_0 + b_1x_1y=b0+b1x1

Trong đó các thành phần bao gồm:

- **y**: Biến phụ thuộc (Dependent Variable) - Giá trị mà chúng ta đang cố gắng dự đoán.
    
- **x₁**: Biến độc lập (Independent Variable) - Biến dùng để dự đoán (Predictor).
    
- **b₀**: Hệ số chặn (Y-intercept) hay còn gọi là hằng số (Constant).
    
- **b₁**: Hệ số góc (Slope coefficient).
    

## Ví dụ minh họa: Nông nghiệp

Áp dụng mô hình để dự đoán sản lượng khoai tây dựa trên lượng phân bón sử dụng.

**Giả định thuật toán tính toán được các giá trị:**

- $b_0 = 8 (tấn)$ 
    
- $b_1 = 3 (tấn/kg)$ 
    
**Phương trình thực tế:**  
Sản lượng=8+3×Lượng phân bón

## Giải thích trực quan trên biểu đồ

![[Chart.png]]

Mô hình được biểu diễn thông qua **biểu đồ phân tán (Scatter plot)**:

- **Các trục tọa độ**:
    
    - Trục hoành (x): Lượng phân bón đạm (Nitrogen fertilizer) sử dụng (đơn vị: kg).
        
    - Trục tung (y): Sản lượng khoai tây (Potato yield) (đơn vị: tấn).
        
- **Điểm dữ liệu (Data points)**: Mỗi điểm đại diện cho một vụ thu hoạch cụ thể, ghi lại lượng phân bón đã dùng và sản lượng thu được tương ứng.
    
- **Đường hồi quy**: Một đường thẳng đi qua các điểm dữ liệu, đại diện cho phương trình phía trên.
    

**Ý nghĩa của các hệ số:**

- **Hệ số chặn (b0=8b_0 = 8b0=8)**: Điểm mà đường thẳng cắt trục tung (Y-intercept).
    
- **Hệ số góc (b1=3b_1 = 3b1=3)**: Thể hiện mức độ thay đổi. Cụ thể, nếu tăng lượng phân bón thêm **1 kg**, sản lượng khoai tây dự kiến sẽ tăng thêm **3 tấn**.