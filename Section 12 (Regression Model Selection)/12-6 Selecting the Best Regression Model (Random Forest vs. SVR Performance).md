## So sánh và Lựa chọn Mô hình Tối ưu (Model Selection Comparison)

Sau khi thiết lập các mẫu mã nguồn `(code templates)` và chạy thử nghiệm trên cùng một bộ dữ liệu, ta tiến hành so sánh hệ số xác định ($R^2$) để xếp hạng hiệu suất.

## 1. Kết quả Thực nghiệm chi tiết

Quy trình chạy thử nghiệm lần lượt trên các mô hình và kết quả thu được:

- **Hồi quy tuyến tính đa biến (Multiple Linear Regression)**
    
    - Hệ số $R^2$: **0.93**
        
    - _Đánh giá_: Mức cơ sở khá tốt.
        
- **Hồi quy đa thức (Polynomial Regression)**
    
    - Thiết lập: Bậc `(degree)` = 4.
        
    - Hệ số $R^2$: **0.9458**
        
    - _Đánh giá_: Hiệu suất cao hơn Hồi quy tuyến tính đa biến.
        
- **Hồi quy Vector hỗ trợ (Support Vector Regression - SVR)**
    
    - Hệ số $R^2$: **0.9480**
        
    - _Đánh giá_: Đánh bại Hồi quy đa thức với khoảng cách nhỏ. Đây là mô hình thường cho kết quả rất tốt.
        
- **Hồi quy Cây quyết định (Decision Tree Regression)**
    
    - Hệ số $R^2$: **0.922**
        
    - _Đánh giá_: Hiệu suất thấp nhất trong các mô hình đã thử (thấp hơn cả Hồi quy tuyến tính đa biến).
        
- **Hồi quy Rừng ngẫu nhiên (Random Forest Regression)**
    
    - Cơ chế: Tập hợp nhiều cây quyết định để đưa ra dự đoán cuối cùng (tinh thần đồng đội).
        
    - Hệ số $R^2$: **0.96**
        
    - _Đánh giá_: **Mô hình chiến thắng (Winner)**.
        

## 2. Phương pháp luận: Cách chọn mô hình tốt nhất?

Câu hỏi thường gặp: _"Làm thế nào để tôi chọn được mô hình tốt nhất cho bài toán của mình?"_

- **Giải pháp**:
    
    1. Sử dụng bộ công cụ tiền xử lý dữ liệu `(data preprocessing toolkit)` để xử lý dữ liệu thiếu hoặc dữ liệu phân loại.
        
    2. Áp dụng các mẫu mã nguồn `(code templates)` để chạy thử tất cả các mô hình trên cùng một tập dữ liệu.
        
    3. So sánh hệ số $R^2$ (hoặc các chỉ số đánh giá khác).
        
    4. Mô hình nào có $R^2$ gần 1 nhất là mô hình tốt nhất.
        
- **Kết luận cho bài toán này**: Với bộ dữ liệu nhà máy điện được sử dụng trong demo, **Random Forest Regression** là lựa chọn tối ưu nhất.
    

## 3. Tổng kết Phần 2: Hồi quy (Regression)

Chúng ta đã hoàn thành nhánh Hồi quy trong Machine Learning với các thành tựu:

- Biết cách xây dựng các mô hình hồi quy khác nhau.
    
- Sở hữu bộ mẫu mã nguồn `(code templates)` linh hoạt cho mọi bộ dữ liệu.
    
- Nắm vững quy trình đánh giá và lựa chọn mô hình dựa trên chỉ số định lượng.
    

> **Bước tiếp theo**: Chuyển sang phần 3 - **Phân loại (Classification)**. Tại đây, chúng ta cũng sẽ xây dựng nhiều mô hình để dự đoán phân loại (category) thay vì giá trị số, và áp dụng quy trình tương tự để chọn ra mô hình tốt nhất.