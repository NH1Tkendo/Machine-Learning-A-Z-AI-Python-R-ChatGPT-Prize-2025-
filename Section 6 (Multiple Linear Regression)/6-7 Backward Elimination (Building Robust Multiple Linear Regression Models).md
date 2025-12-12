## Tổng quan về Xây dựng Mô hình (Model Building)

## Tại sao cần chọn lọc biến?

Trong thực tế, dữ liệu thường có rất nhiều cột (biến). Không phải lúc nào cũng nên đưa tất cả các biến vào mô hình hồi quy vì hai lý do chính:

1. **Rác vào, rác ra (Garbage in, Garbage out):** Nếu đưa quá nhiều dữ liệu không liên quan vào, mô hình sẽ trở nên kém tin cậy và hoạt động không hiệu quả.
    
2. **Khả năng giải thích (Interpretability):** Bạn cần giải thích các biến số và sự tác động của chúng đối với biến phụ thuộc cho cấp quản lý hoặc khách hàng. Việc giải thích một mô hình với hàng nghìn biến là không khả thi; chỉ nên giữ lại những biến dự báo quan trọng nhất.
    

## 5 Phương pháp xây dựng mô hình

Có 5 phương pháp chính để lựa chọn biến và xây dựng mô hình:

1. **Tất cả cùng vào** (All-in)
    
2. **Loại bỏ lùi** (Backward Elimination)
    
3. **Lựa chọn tiến** (Forward Selection)
    
4. **Loại bỏ hai chiều** (Bidirectional Elimination) - Thường được gọi là _Hồi quy từng bước (Stepwise Regression)_.
    
5. **So sánh điểm số** (Score Comparison) hay _Tất cả mô hình khả thi (All Possible Models)_.
    

---

## Chi tiết các phương pháp

## 1. Tất cả cùng vào (All-in)

Phương pháp này đơn giản là đưa tất cả các biến vào mô hình.

- **Khi nào sử dụng?**
    
    - **Kiến thức có trước (Prior Knowledge):** Bạn đã biết chắc chắn những biến nào là yếu tố dự báo thực sự.
        
    - **Yêu cầu bắt buộc:** Có quy định (ví dụ: quy định ngân hàng) yêu cầu phải sử dụng các biến cụ thể này.
        
    - **Bước đệm:** Làm bước chuẩn bị cho phương pháp _Loại bỏ lùi (Backward Elimination)_.
        

## 2. Loại bỏ lùi (Backward Elimination)

Đây là phương pháp nhanh và hiệu quả, sẽ được tập trung thực hành trong khóa học.

- **Bước 1:** Chọn mức ý nghĩa thống kê để giữ lại trong mô hình (Significance Level to stay), ví dụ: $SL = 0.05$.
    
- **Bước 2:** Khớp mô hình đầy đủ (fit the full model) với tất cả các biến dự báo có thể.
    
- **Bước 3:** Xem xét biến dự báo có **P-value cao nhất**. Nếu $P > SL$, chuyển sang Bước 4. Nếu không, kết thúc (FIN).
    
- **Bước 4:** Loại bỏ biến dự báo đó khỏi mô hình.
    
- **Bước 5:** Khớp lại mô hình (Fit the model) mà không có biến vừa loại bỏ. (Lưu ý: Phải chạy lại mô hình để cập nhật các hệ số).
    
- **Vòng lặp:** Quay lại Bước 3 và lặp lại cho đến khi không còn biến nào có $P > SL$.
    
![[LoaiBoLui-BackwardElimination.png]]
## 3. Lựa chọn tiến (Forward Selection)

Quy trình ngược lại và phức tạp hơn so với Loại bỏ lùi.

- **Bước 1:** Chọn mức ý nghĩa thống kê để đưa vào mô hình (Significance Level to enter), ví dụ: $SL = 0.05$.
    
- **Bước 2:** Khớp tất cả các mô hình hồi quy đơn (simple regression models) có thể ($y$ với từng $x_n$). Chọn biến có **P-value thấp nhất**.
    
- **Bước 3:** Giữ biến đã chọn, khớp tất cả các mô hình có thể với thêm **một** biến dự báo khác.
    
- **Bước 4:** Chọn biến mới có P-value thấp nhất trong các mô hình vừa chạy. Nếu $P < SL$, quay lại Bước 3 (tiếp tục thêm biến).
    
- **Kết thúc:** Nếu biến mới có $P > SL$, dừng lại. Giữ lại mô hình **trước đó** (không bao gồm biến vừa thêm vào).
    
![[LuaChonTien-ForwardSelection.png]]
## 4. Loại bỏ hai chiều (Bidirectional Elimination)

Thường được gọi chung là **Stepwise Regression**. Kết hợp cả hai phương pháp trên.

- **Bước 1:** Chọn mức ý nghĩa để đưa vào ($P_{enter}$) và mức ý nghĩa để giữ lại ($P_{stay}$), ví dụ: $P = 0.05$ cho cả hai.
    
- **Bước 2:** Thực hiện bước tiếp theo của _Lựa chọn tiến_ (thêm biến mới có ý nghĩa).
    
- **Bước 3:** Thực hiện tất cả các bước của _Loại bỏ lùi_ (loại bỏ biến cũ nếu chúng trở nên không còn ý nghĩa sau khi thêm biến mới).
    
- **Vòng lặp:** Lặp lại cho đến khi không thể thêm biến mới và cũng không thể loại bỏ biến cũ nào.
    
![[LoaiBoHaiChieu-BidirectionalElimination.png]]
## 5. So sánh điểm số (Score Comparison / All Possible Models)

Phương pháp này kỹ lưỡng nhất nhưng tốn kém tài nguyên nhất.

- **Bước 1:** Chọn một tiêu chí đánh giá độ phù hợp (Goodness of fit), ví dụ: Tiêu chí Akaike, $R^2$, v.v.
    
- **Bước 2:** Xây dựng **tất cả** các mô hình hồi quy có thể từ các biến đang có.
    
    - Công thức số lượng mô hình: $2^n - 1$ (với $n$ là số lượng biến).
        
    - Ví dụ: 10 biến $\rightarrow$ 1023 mô hình.
        
- **Bước 3:** Chọn mô hình có tiêu chí tốt nhất.
    
- **Nhược điểm:** Khối lượng tính toán tăng theo cấp số nhân, không khả thi với các tập dữ liệu lớn.
![[SoSanhDemSo-AllPossibeModels.png]]

---

## Kết luận

Trong khóa học này, chúng ta sẽ tập trung thực hành phương pháp **Loại bỏ lùi (Backward Elimination)** vì đây là phương pháp:

- Nhanh nhất trong các phương pháp từng bước.
    
- Dễ hiểu và dễ thực hiện.
    
- Vẫn đảm bảo tạo ra một mô hình mạnh mẽ và loại bỏ các biến không cần thiết.