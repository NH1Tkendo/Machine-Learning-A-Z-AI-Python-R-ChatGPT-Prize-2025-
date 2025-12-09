## Co giãn Đặc trưng (Feature Scaling)

Co giãn đặc trưng là một bước tiền xử lý quan trọng trong học máy, giúp đưa các đặc trưng (features) về cùng một thang đo để tránh một đặc trưng nào đó lấn át các đặc trưng khác.

## Nguyên tắc áp dụng

- Co giãn đặc trưng **luôn được áp dụng trên các cột** (columns) của dữ liệu.
    
- Nó không bao giờ được áp dụng theo hàng (rows).
    

## Các kỹ thuật co giãn đặc trưng chính

Có hai kỹ thuật phổ biến nhất để thực hiện co giãn đặc trưng:
![[ChuanHoa-TieuChuanHoa.png]]

- **Chuẩn hóa (Normalization)**: Kỹ thuật này sẽ biến đổi các giá trị trong một cột để chúng nằm trong khoảng từ 0 đến 1.
    
    - Công thức: `(giá trị - giá trị nhỏ nhất) / (giá trị lớn nhất - giá trị nhỏ nhất)`
        
- **Tiêu chuẩn hóa (Standardization)**: Kỹ thuật này sẽ biến đổi dữ liệu sao cho phân phối của nó có giá trị trung bình là 0 và độ lệch chuẩn là 1. Kết quả là hầu hết các giá trị sẽ nằm trong khoảng từ -3 đến 3.
    
    - Công thức: `(giá trị - giá trị trung bình) / độ lệch chuẩn`
        
    - _Ghi chú_: Các giá trị ngoại lệ (outliers) cực lớn có thể nằm ngoài khoảng [-3, 3].
        

## Tại sao co giãn đặc trưng lại quan trọng?

Để hiểu tầm quan trọng của việc này, hãy xét một ví dụ đơn giản về việc so sánh sự tương đồng giữa các đối tượng.

## Ví dụ minh họa

Giả sử ta có một tập dữ liệu về thu nhập hàng năm và tuổi của 3 người khác nhau. Nhiệm vụ là xác định xem người màu tím (purple) giống với người màu xanh dương (blue) hay người màu đỏ (red) hơn.

|Người|Thu nhập (Income)|Tuổi (Age)|
|---|---|---|
|Xanh dương (Blue)|$70,000|45|
|Tím (Purple)|$60,000|44|
|Đỏ (Red)|$52,000|40|

## Phân tích khi chưa co giãn

- **Chênh lệch Thu nhập**:
    
    - Tím vs. Xanh dương: $10,000
        
    - Tím vs. Đỏ: $8,000
        
- **Chênh lệch Tuổi**:
    
    - Tím vs. Xanh dương: 1 năm
        
    - Tím vs. Đỏ: 4 năm
        

Nếu không co giãn, các giá trị của cột "Thu nhập" (ví dụ: 10,000 và 8,000) lớn hơn rất nhiều so với cột "Tuổi" (1 và 4). Điều này có thể khiến thuật toán đánh giá sai rằng sự chênh lệch về thu nhập quan trọng hơn và kết luận người Tím giống người Đỏ hơn (vì chênh lệch $8,000 nhỏ hơn $10,000). Đây là vấn đề "so sánh táo với cam" vì các đơn vị và thang đo hoàn toàn khác nhau.

## Phân tích sau khi áp dụng Chuẩn hóa (Normalization)

Sau khi áp dụng chuẩn hóa, tất cả các giá trị của cả hai cột "Thu nhập" và "Tuổi" đều được đưa về cùng một thang đo (từ 0 đến 1).

- Các giá trị sau khi chuẩn hóa cho phép so sánh một cách công bằng ("like for like").
    
- Lúc này, có thể thấy rõ rằng về mặt tuổi tác, người Tím rất gần với người Xanh dương. Về thu nhập, người Tím nằm ở khoảng giữa hai người còn lại.
    
- Việc co giãn đặc trưng giúp các thuật toán (đặc biệt là các thuật toán dựa trên khoảng cách như Phân cụm - Clustering) đưa ra kết luận chính xác hơn.