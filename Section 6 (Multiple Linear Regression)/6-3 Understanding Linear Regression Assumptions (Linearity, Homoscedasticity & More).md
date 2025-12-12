## Các giả định của Hồi quy tuyến tính (Assumptions of Linear Regression)

Trước khi xây dựng mô hình, cần đảm bảo dữ liệu phù hợp để áp dụng hồi quy tuyến tính. Ví dụ về **bộ tứ Anscombe (Anscombe's quartet)** cho thấy 4 tập dữ liệu khác nhau có thể tạo ra cùng một đường hồi quy, nhưng mô hình có thể hoàn toàn sai lệch nếu không thỏa mãn các giả định dưới đây .

Có 5 giả định chính và 1 bước kiểm tra bổ sung:

## 1. Tính tuyến tính (Linearity)

- Phải tồn tại mối quan hệ tuyến tính giữa biến phụ thuộc (dependent variable) và mỗi biến độc lập (independent variable).

- Nếu dữ liệu phân bố phi tuyến tính, mô hình hồi quy tuyến tính sẽ đưa ra kết quả sai lệch.

![[TinhTuyenTinh_Linearity.png]]

## 2. Đồng nhất phương sai (Homoscedasticity)

- Thuật ngữ này có nghĩa là "phương sai bằng nhau" (equal variance).
    
- **Yêu cầu**: Trên biểu đồ phân tán của sai số, không được xuất hiện hình dạng chiếc nón (cone shape) – dù là nón mở rộng hay thu hẹp.
    
- Nếu xuất hiện hình nón, điều đó có nghĩa phương sai đang phụ thuộc vào biến độc lập, vi phạm giả định này.
    
![[DongNhatPhuongSai-Homoscedasticity.png]]
## 3. Phân phối chuẩn đa biến (Multivariate Normality)

- Còn được gọi là tính chuẩn của phân phối sai số (normality of error distribution).
    
- **Cách hiểu trực quan**: Khi nhìn dọc theo đường hồi quy, các điểm dữ liệu nên phân bố theo dạng phân phối chuẩn (hình chuông) xung quanh đường đó.
    
![[PhanPhoiChuanDaBien-MultivariateNormality.png]]
## 4. Sự độc lập của các quan sát (Independence of observations)

- Thường được gọi là **Không có tự tương quan (No autocorrelation)**.
    
- **Yêu cầu**: Không được có bất kỳ quy luật (pattern) nào trong việc phân bố các quan sát. Các hàng dữ liệu phải độc lập, hàng này không được ảnh hưởng tới hàng kia.
    
- **Ví dụ vi phạm điển hình**: Dữ liệu thị trường chứng khoán, nơi giá của ngày hôm trước ảnh hưởng đến giá ngày hôm sau.
    
![[SuDocLapCuaQuanSat-Independence.png]]
## 5. Không có đa cộng tuyến (Lack of Multicollinearity)

- **Yêu cầu**: Các biến độc lập (predictors) không được có sự tương quan mạnh với nhau.
    
- Nếu các biến độc lập tương quan với nhau, các ước lượng hệ số (coefficient estimates) trong mô hình sẽ trở nên không đáng tin cậy (unreliable).
    
![[DaCongTuyen-LackOfMulticollinearity.png]]
## 6. Kiểm tra giá trị ngoại lai (Outlier check)

_Đây là bước kiểm tra thêm, không phải là một giả định lý thuyết nhưng rất quan trọng._

- Các giá trị ngoại lai (outliers) có thể kéo lệch đường hồi quy một cách đáng kể.
    
- **Hành động**: Dựa vào kiến thức nghiệp vụ và dữ liệu thực tế để quyết định nên **loại bỏ** hay **giữ lại** các giá trị này trước khi chạy mô hình.
    
![[KiemTraGiaTriNgoaiLai-OutlierCheck.png]]
---

**Tài liệu tham khảo thêm**:  
Bạn có thể tải xuống tóm tắt các giả định này dưới dạng Poster PDF tại: [superdatascience.com/assumptions](https://www.superdatascience.com/assumptions) .