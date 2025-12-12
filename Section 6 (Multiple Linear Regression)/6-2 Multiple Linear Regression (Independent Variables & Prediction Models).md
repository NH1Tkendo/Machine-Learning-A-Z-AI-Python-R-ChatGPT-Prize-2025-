## Hồi quy tuyến tính đa biến (Multiple Linear Regression)

## Phương trình tổng quát

Phương trình của hồi quy tuyến tính đa biến có cấu trúc tương tự như hồi quy tuyến tính đơn biến, nhưng bao gồm nhiều cặp hệ số và biến số hơn. Về cơ bản, số lượng hệ số góc sẽ tương ứng với số lượng biến độc lập .

Công thức tổng quát có thể được biểu diễn như sau:

$y = b_0 + m_1x_1 + m_2x_2 + ... + m_nx_n$

Trong đó:

- **$y$**: Biến phụ thuộc (dependent variable).
    
- **$b_0$**: Hệ số chặn (y-intercept) hoặc hằng số (constant).
    
- **$m_1, m_2, ...$**: Các hệ số góc (slope coefficients) tương ứng với từng biến.
    
- **$x_1, x_2, ...$**: Các biến độc lập (independent variables).
    

## Ví dụ thực tế: Dự đoán sản lượng khoai tây

Để minh họa, ta xem xét bài toán dự đoán sản lượng khoai tây dựa trên các yếu tố môi trường và canh tác .

Các biến độc lập được sử dụng bao gồm:

1. Lượng phân bón Nitơ sử dụng (kg).
    
2. Nhiệt độ trung bình trong mùa vụ (độ C).
    
3. Lượng mưa (mm).
    

Phương trình dự đoán mẫu:

$Sản_lượng = 8 + 3 \times Nitơ - 0.54 \times Nhiệt_độ + 0.04 \times Lượng_mưa$

**Giải thích các hệ số:**

- **$8$ (Hệ số chặn)**: Mức sản lượng cơ sở (tấn).
    
- **$3$ (Hệ số phân bón)**: Tương ứng với mỗi kg phân bón tăng thêm, sản lượng tăng 3 tấn.
    
- **$-0.54$ (Hệ số nhiệt độ)**: Dấu âm biểu thị mối quan hệ nghịch đảo; nhiệt độ càng cao, sản lượng khoai tây càng giảm (giảm 0.54 tấn cho mỗi độ C tăng thêm).
    
- **$0.04$ (Hệ số lượng mưa)**: Tương ứng với mỗi mm nước mưa, sản lượng tăng 0.04 tấn.
    

## Tài liệu tham khảo thêm

Để tìm hiểu sâu hơn về ứng dụng thực tế của hồi quy tuyến tính đa biến trong nông nghiệp, bạn có thể tham khảo bài nghiên cứu sau :

- **Tên bài báo**: _"The Application of Multiple Linear Regression and Artificial Neural Network Models for Yield Prediction of Very Early Potato Cultivars before Harvest"_.
    
- **Nội dung**: Bài báo kết hợp và so sánh hai mô hình là hồi quy tuyến tính đa biến và mạng nơ-ron nhân tạo (Artificial Neural Network) trong việc dự đoán năng suất.