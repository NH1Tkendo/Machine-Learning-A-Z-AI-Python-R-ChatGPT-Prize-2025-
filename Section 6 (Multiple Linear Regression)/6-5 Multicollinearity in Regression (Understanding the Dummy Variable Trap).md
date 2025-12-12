## Bẫy biến giả (Dummy Variable Trap)

## Khái niệm và Vấn đề

Trong bài học trước, chúng ta đã biết quy tắc: **Không bao giờ đưa cả hai biến giả vào mô hình cùng một lúc** (ví dụ: đưa cả cột New York và cột California). Nếu làm vậy, ta sẽ rơi vào "Bẫy biến giả".

- **Hiện tượng Đa cộng tuyến (Multicollinearity):** Đây là hiện tượng mà một hoặc nhiều biến độc lập trong mô hình hồi quy có thể dự đoán được lẫn nhau một cách tuyến tính.
    
- **Hệ quả:** Mô hình không thể phân biệt được tác động riêng lẻ của từng biến giả (ví dụ: tác động của $D_1$ so với $D_2$). Về mặt toán học, mô hình sẽ không thể tính toán chính xác các hệ số hồi quy do sự xung đột giữa các biến giả và hằng số (_constant_).
    

## Nguyên nhân toán học

Mối quan hệ giữa hai biến giả luôn mang tính trực tiếp và cố định. Nếu ta có hai trạng thái (New York và California), thì:

$D2=1−D1D_2 = 1 - D_1D2=1−D1$

Trong đó:

- $D_1$: Biến giả đại diện cho New York.
    
- $D_2$: Biến giả đại diện cho California.
    

Vì $D_2$ hoàn toàn phụ thuộc vào $D_1$, việc đưa cả hai vào mô hình là dư thừa thông tin và gây lỗi mô hình.

## Quy tắc thực hành

Để tránh bẫy biến giả, luôn tuân thủ nguyên tắc loại bỏ một biến:

1. **Quy tắc $N - 1$:**  
    Nếu biến phân loại gốc có $N$ nhóm (categories), bạn chỉ được đưa **$N - 1$** biến giả vào mô hình.
    
    - _Ví dụ 1:_ Có 2 bang $\rightarrow$ Dùng 1 biến giả.
        
    - _Ví dụ 2:_ Có 9 phân loại $\rightarrow$ Dùng 8 biến giả.
        
    - _Ví dụ 3:_ Có 100 phân loại $\rightarrow$ Dùng 99 biến giả.
        
2. **Áp dụng cho nhiều bộ biến giả:**  
    Nếu tập dữ liệu có nhiều cột phân loại khác nhau (ví dụ: vừa có cột "Bang", vừa có cột "Ngành nghề"), bạn cần áp dụng quy tắc $N - 1$ cho **từng bộ riêng biệt**.
    
    - Tạo bộ biến giả cho "Bang" $\rightarrow$ Loại bỏ 1 biến của bang.
        
    - Tạo bộ biến giả cho "Ngành nghề" $\rightarrow$ Loại bỏ 1 biến của ngành nghề.
        

## Kết luận

Luôn nhớ loại bỏ 1 biến giả đại diện (làm trạng thái mặc định) cho mỗi nhóm phân loại khi xây dựng mô hình hồi quy để đảm bảo tính chính xác và tránh hiện tượng đa cộng tuyến.