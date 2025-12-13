
## Tổng quan về Hồi quy Đa thức (Polynomial Regression)

Trong Machine Learning, Hồi quy Đa thức là một kỹ thuật mở rộng từ các mô hình hồi quy cơ bản để xử lý các dữ liệu có mối quan hệ phi tuyến tính.

## So sánh các công thức Hồi quy

Để hiểu rõ bản chất, ta so sánh công thức của ba loại hồi quy:

1. **Hồi quy Tuyến tính Đơn (Simple Linear Regression):**  
    Sử dụng một biến độc lập duy nhất.  
    y=b0+b1x1y = b_0 + b_1x_1y=b0+b1x1
    
2. **Hồi quy Tuyến tính Đa biến (Multiple Linear Regression):**  
    Sử dụng nhiều biến độc lập khác nhau ($x_1, x_2, \dots, x_n$).  
    y=b0+b1x1+b2x2+⋯+bnxny = b_0 + b_1x_1 + b_2x_2 + \dots + b_nx_ny=b0+b1x1+b2x2+⋯+bnxn
    
3. **Hồi quy Đa thức (Polynomial Linear Regression):**  
    Tương tự như Hồi quy Đa biến, nhưng thay vì sử dụng các biến khác nhau, nó sử dụng **cùng một biến** ($x_1$) nhưng ở các **lũy thừa (powers)** khác nhau.  
    $y = b_0 + b_1x_1 + b_2x_1^2 + \dots + b_nx_1^ny=b0+b1x1+b2x12+⋯+bnx1n$
    
![[HoiQuyDaThuc-PLR.png]]
## Khi nào sử dụng Hồi quy Đa thức?

Mô hình này hữu ích khi dữ liệu không phân bố theo một đường thẳng mà có hình dạng cong (ví dụ: hình parabol).

## Vấn đề của Hồi quy Tuyến tính Đơn

- Nếu áp dụng đường thẳng ($y = b_0 + b_1x_1$) vào tập dữ liệu có dạng cong:
    
    - Đường hồi quy sẽ không khớp tốt với dữ liệu (fitting poorly).
        
    - Dữ liệu có thể nằm dưới đường thẳng ở đoạn giữa và nằm trên đường thẳng ở các đoạn xa hơn.
        

## Giải pháp Hồi quy Đa thức

- Khi thêm các bậc cao hơn của $x$ (ví dụ: $x^2$), đường hồi quy sẽ có độ cong (parabolic effect).
    
- **Công thức ví dụ bậc 2:**  
    y=b0+b1x1+b2x12y = b_0 + b_1x_1 + b_2x_1^2y=b0+b1x1+b2x12  
    Biến số $b_2x_1^2$ tạo ra hiệu ứng đường cong parabol, giúp mô hình khớp chặt chẽ hơn với dữ liệu thực tế.
    

## Ứng dụng thực tế

- Mô tả sự lây lan của dịch bệnh (bệnh truyền nhiễm, đại dịch).
    
- Các trường hợp dữ liệu tăng trưởng hoặc suy giảm theo hàm mũ hoặc đa thức.
    

## Tại sao vẫn gọi là "Hồi quy Tuyến tính" (Linear)?

Mặc dù mối quan hệ giữa biến $x$ và $y$ là **phi tuyến tính** (non-linear) do sự xuất hiện của $x^2, x^3\dots$, mô hình này vẫn thuộc lớp **Hồi quy Tuyến tính**.

## Lý do kỹ thuật

- Khái niệm "Tuyến tính" hay "Phi tuyến tính" trong lớp các bài toán hồi quy đề cập đến các **hệ số (coefficients)** ($b_0, b_1, b_2\dots$), không phải biến $x$.
    
- Hàm số được coi là tuyến tính nếu nó có thể được biểu diễn dưới dạng **tổ hợp tuyến tính (linear combination)** của các hệ số.
    
- Mục tiêu của thuật toán là tìm ra các hệ số ẩn $b$. Miễn là phương trình là tuyến tính đối với các hệ số này, nó vẫn được gọi là Hồi quy Tuyến tính.
    

## Ví dụ về Hồi quy Phi tuyến tính (Non-linear Regression)

Một phương trình được coi là phi tuyến tính thực sự khi không thể tách biệt các hệ số theo dạng tổ hợp tuyến tính. Ví dụ:  
y=b0+b1x1b2+x2y = \frac{b_0 + b_1x_1}{b_2 + x_2}y=b2+x2b0+b1x1  
Trong trường hợp này, không thể thay thế hoặc biến đổi để đưa về dạng tuyến tính của các hệ số $b$.

## Kết luận

- Hồi quy Đa thức thực chất là một **trường hợp đặc biệt (special case)** của Hồi quy Tuyến tính Đa biến.
    
- Đây không phải là một loại hồi quy hoàn toàn mới, mà là một cách áp dụng linh hoạt của mô hình đa biến với các biến số là lũy thừa của cùng một đại lượng.
