## Hệ số R bình phương (R Squared)

## Khái niệm

**R Squared ($R^2$)** là một chỉ số thống kê dùng để đánh giá độ phù hợp (goodness of fit) của một mô hình hồi quy. Nó cho biết mức độ mà mô hình của bạn giải thích được sự biến thiên của dữ liệu so với một mô hình đơn giản nhất (đường trung bình).

## Cơ sở tính toán: So sánh hai mô hình

Để hiểu $R^2$, ta cần so sánh sai số giữa đường hồi quy ta xây dựng và đường trung bình cơ bản.

## 1. Tổng bình phương phần dư (Residual Sum of Squares - $SS_{res}$)

Đây là sai số của **đường hồi quy (Regression Line)** mà mô hình xây dựng (sử dụng phương pháp Bình phương tối thiểu - OLS).

- Ta chiếu các điểm dữ liệu thực tế ($y_i$) lên đường hồi quy để tìm giá trị dự đoán ($\hat{y}_i$).
    
- Công thức tính tổng bình phương sai lệch:  
    $SS_{res} = \sum (y_i - \hat{y}_i)^2$
    
![[SumOfSquare.png]]
## 2. Tổng bình phương toàn phần (Total Sum of Squares - $SS_{tot}$)

Đây là sai số của **đường trung bình (Average Line)**. Đây là mô hình sơ khai nhất, chỉ đơn giản là lấy giá trị trung bình của tất cả dữ liệu ($y_{avg}$) để dự đoán.

- Ta chiếu các điểm dữ liệu thực tế ($y_i$) lên đường trung bình.
    
- Công thức tính tổng bình phương sai lệch:  
    $SS_{tot} = \sum (y_i - y_{avg})^2$
    
![[TotalSumOfSquares.png]]
## Công thức R Squared

Hệ số $R^2$ được tính bằng cách so sánh hai giá trị trên:

$R^2 = 1 - \frac{SS_{res}}{SS_{tot}}$

**Giải thích ý nghĩa:**

- Thông thường, đường hồi quy sẽ khớp dữ liệu tốt hơn đường trung bình, do đó $SS_{res} < SS_{tot}$.
    
- Điều này khiến tỷ số $\frac{SS_{res}}{SS_{tot}}$ nhỏ hơn 1, và $R^2$ sẽ nằm trong khoảng từ 0 đến 1.
    
- $SS_{res}$ càng nhỏ (mô hình càng khớp) $\rightarrow$ $R^2$ càng tiến về 1.
    

## Quy tắc đánh giá nhanh (Rule of Thumb)

Dưới đây là các mốc tham khảo để đánh giá chất lượng mô hình dựa trên $R^2$ (lưu ý: phụ thuộc nhiều vào bối cảnh bài toán cụ thể):

- **$R^2 = 1$**: Hoàn hảo (Perfect fit). Điều này rất đáng ngờ và hầu như không xảy ra trong thực tế.
    
- **$R^2 \approx 0.9$**: Mô hình rất tốt (Very good).
    
- **$R^2 < 0.7$**: Mô hình chưa tốt lắm (Not great).
    
- **$R^2 < 0.4$**: Mô hình tệ (Terrible).
    
- **$R^2 < 0$**: Mô hình hoàn toàn vô nghĩa. Điều này xảy ra khi đường hồi quy dự đoán còn tệ hơn cả việc chỉ lấy trung bình (ví dụ: dữ liệu hướng lên nhưng mô hình lại vẽ đường hướng xuống).