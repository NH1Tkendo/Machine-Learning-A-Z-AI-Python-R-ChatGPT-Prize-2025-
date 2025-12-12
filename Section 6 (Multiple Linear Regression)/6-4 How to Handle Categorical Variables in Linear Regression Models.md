## Biến giả (Dummy Variables)

## Bối cảnh và Vấn đề

Trong bài toán phân tích lợi nhuận của các công ty khởi nghiệp (startup), chúng ta có tập dữ liệu bao gồm:

- **Biến phụ thuộc (Dependent Variable):** Lợi nhuận (_Profit_ - $Y$).
    
- **Biến độc lập (Independent Variables):**
    
    - Chi phí R&D (_R&D Spend_ - $X_1$)
        
    - Chi phí quản lý (_Admin Spend_ - $X_2$)
        
    - Chi phí tiếp thị (_Marketing Spend_ - $X_3$)
        
    - Bang hoạt động (_State_): New York hoặc California.
        

**Thách thức:** Quỹ đầu tư mạo hiểm muốn tìm mối tương quan giữa lợi nhuận và các biến trên để xây dựng mô hình _Hồi quy tuyến tính (Linear Regression)_. Tuy nhiên, phương trình hồi quy chỉ làm việc với các con số, trong khi biến "State" là một _biến phân loại (categorical variable)_ chứa dữ liệu dạng chữ.

## Giải pháp: Tạo Biến giả (Dummy Variables)

Để đưa _biến phân loại_ vào phương trình hồi quy, ta cần chuyển đổi chúng thành các con số thông qua phương pháp tạo biến giả.

## Quy trình thực hiện:

1. **Xác định các phân loại:** Tìm tất cả các giá trị khác nhau trong cột _State_ (Ví dụ: New York và California).
    
2. **Tạo cột mới:** Tạo thêm các cột mới tương ứng với mỗi phân loại (cột "New York", cột "California").
    
3. **Gán giá trị nhị phân (Binary):**
    
    - Nếu dòng dữ liệu có State là "New York": Điền số **1** vào cột New York, số **0** vào cột California.
        
    - Nếu dòng dữ liệu có State là "California": Điền số **1** vào cột California, số **0** vào cột New York.
        

## Xây dựng Mô hình Hồi quy

Sau khi tạo biến giả, ta không sử dụng cột _State_ ban đầu nữa. Tuy nhiên, quy tắc quan trọng là **không bao giờ đưa tất cả các biến giả vào mô hình**.

Ta chỉ chọn 1 trong 2 cột biến giả để đưa vào phương trình (ví dụ: chọn cột New York, bỏ cột California).

**Phương trình hồi quy đa biến:**

$Y= b_0 + b_1X_1 + b_2X_2 + b_3X_3 + b_4D_1Y=b0+b1X1+b2X2+b3X3+b4D1$

Trong đó:

- $Y$: Lợi nhuận (_Profit_)
    
- $b_0$: Hằng số (_Constant_)
    
- $b_1, b_2, b_3, b_4$: Các hệ số (_Coefficients_)
    
- $X_1, X_2, X_3$: Các biến chi phí (R&D, Admin, Marketing)
    
- $D_1$: Biến giả cho New York (1 nếu là NY, 0 nếu là CA)
    

## Cơ chế hoạt động và Ý nghĩa

Tại sao chỉ cần dùng một biến giả (New York) mà không sợ mất dữ liệu về California hay gây ra thiên kiến (bias)?

## 1. Nguyên lý công tắc đèn (Light Switch)

Biến giả hoạt động như một công tắc:

- Nếu $D_1 = 1$: Công tắc BẬT $\rightarrow$ Công ty ở New York.
    
- Nếu $D_1 = 0$: Công tắc TẮT $\rightarrow$ Mặc định công ty không ở New York (tức là ở California).  
    $\rightarrow$ Thông tin vẫn được bảo toàn đầy đủ.
    

## 2. Trạng thái mặc định (Default State)

Việc không có hệ số riêng cho California không có nghĩa là nó bị bỏ qua hay thiên vị:

- **Trạng thái mặc định:** Biến bị loại bỏ (California) trở thành trạng thái mặc định của mô hình.
    
- **Hệ số:** Tác động của California được gộp vào hằng số $b_0$.
    
- **Hệ số $b_4$:** Biểu thị sự chênh lệch hoặc thay đổi từ trạng thái mặc định (California) sang trạng thái mới (New York).
    

> **Lưu ý:** Nếu đưa cả hai biến giả vào mô hình sẽ dẫn đến hiện tượng _Bẫy biến giả (Dummy Variable Trap)_, gây lỗi đa cộng tuyến (sẽ được bàn ở bài sau).