## Phương pháp Bình phương Tối thiểu (Ordinary Least Squares - OLS)

## Vấn đề cần giải quyết

Khi có một tập hợp các điểm dữ liệu trên biểu đồ phân tán, chúng ta có thể vẽ rất nhiều đường thẳng khác nhau đi qua các điểm đó. Mục tiêu là phải xác định được:

- Đường thẳng nào phù hợp nhất (best fit line)?
    
- Tiêu chí cụ thể để định nghĩa sự "tốt nhất" là gì?
    
![[OLS.png]]
## Các thành phần trong so sánh

Để đánh giá, ta so sánh sự khác biệt giữa dữ liệu thực tế và dữ liệu do đường thẳng mô hình dự đoán tại cùng một điểm đầu vào (trục hoành).

- **$y_i$: **Giá trị thực tế (Actual value/Observed value)**.
    
    - Là dữ liệu thật sự thu thập được.
        
    - _Ví dụ:_ Sử dụng 15kg phân bón, thực tế thu hoạch được **2 tấn** khoai tây.
        
- **$\hat{y}_i$**: **Giá trị dự đoán (Predicted value)**.
    
    - Là giá trị nằm trên đường hồi quy mà mô hình đưa ra.
        
    - _Ví dụ:_ Với cùng 15kg phân bón, đường hồi quy dự đoán thu được **1.5 tấn**.
        

## Phần dư (Residual)

- Là chênh lệch giữa giá trị thực tế và giá trị dự đoán.
    
- Công thức: $\text{Residual} = y_i - \hat{y}_i$
    
- _Lưu ý:_ Việc đường thẳng không đi qua chính xác tất cả các điểm dữ liệu là điều bình thường trong thực tế.
    

## Nguyên lý hoạt động của OLS

Phương pháp "Bình phương Tối thiểu" (Ordinary Least Squares) xác định đường hồi quy tốt nhất dựa trên quy tắc sau:

1. Tính phần dư cho **mọi** điểm dữ liệu.
    
2. **Bình phương** từng phần dư (để loại bỏ số âm và nhấn mạnh các sai số lớn).
    
3. Tính **tổng** của tất cả các bình phương này.
    

**Kết luận:**  
Đường hồi quy tốt nhất là đường có các tham số $b_0$ và $b_1$ sao cho **Tổng bình phương các phần dư (Sum of the squares of the residuals)** đạt giá trị **nhỏ nhất** (minimized).