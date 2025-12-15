## Hệ số R bình phương hiệu chỉnh (Adjusted R Squared)

## Vấn đề của R Squared thông thường

Mặc dù $R^2$ là công cụ tốt để đo độ phù hợp, nó gặp phải một vấn đề lớn khi ta thêm các biến độc lập mới vào mô hình:

- **Xu hướng luôn tăng**: Khi thêm một biến mới (ví dụ $X_3$) vào mô hình:
    
    - Tổng bình phương toàn phần ($SS_{tot}$) không đổi.
        
    - Tổng bình phương phần dư ($SS_{res}$) sẽ **giảm hoặc giữ nguyên**, chứ không bao giờ tăng.
        
- **Nguyên nhân**: Thuật toán Bình phương tối thiểu (OLS) luôn cố gắng tìm hệ số ($b_3$) để tối thiểu hóa sai số.
    
    - Nếu biến mới giúp dự đoán tốt hơn $\rightarrow$ $SS_{res}$ giảm $\rightarrow$ $R^2$ tăng.
        
    - Nếu biến mới không có ích $\rightarrow$ OLS sẽ đặt hệ số $b_3 = 0$ để loại bỏ tác động $\rightarrow$ $R^2$ giữ nguyên.
        
- **Hệ quả**: Ta có thể thêm hàng tá biến vô nghĩa vào mô hình mà $R^2$ vẫn tăng (do các tương quan ngẫu nhiên), dẫn đến đánh giá sai lệch về chất lượng mô hình.
    

## Giải pháp: Adjusted R Squared

Để khắc phục tình trạng "lạm phát" điểm số khi thêm biến, ta sử dụng **Adjusted R Squared**. Chỉ số này phạt mô hình nếu thêm các biến không cần thiết.

## Công thức

$R^2_{adj} = 1 - (1 - R^2) \times \frac{n - 1}{n - k - 1}$

Trong đó:

- $n$: Kích thước mẫu (số lượng quan sát).
    
- $k$: Số lượng biến độc lập trong mô hình.
    

## Cơ chế hoạt động

- Yếu tố **$k$** nằm ở mẫu số. Khi thêm biến mới $\rightarrow$ $k$ tăng $\rightarrow$ mẫu số $(n - k - 1)$ giảm $\rightarrow$ toàn bộ phân số tăng lên.
    
- Vì phân số này bị trừ đi từ 1, nên kết quả **$R^2_{adj}$ sẽ giảm xuống**.
    
- **Ý nghĩa**: Việc thêm một biến mới chỉ được coi là "đáng giá" nếu nó làm tăng $R^2$ gốc đủ lớn để bù đắp lại "án phạt" do việc tăng $k$ gây ra.
    

## Kết luận

- **Adjusted R Squared** giúp đảm bảo rằng ta chỉ thêm các biến thực sự mang lại giá trị cải thiện đáng kể cho mô hình.
    
- Đây là chỉ số tin cậy hơn $R^2$ khi so sánh các mô hình có số lượng biến khác nhau.