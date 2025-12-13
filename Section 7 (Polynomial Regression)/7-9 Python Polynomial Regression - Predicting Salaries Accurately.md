## 2. Dự đoán bằng Hồi quy Đa thức (Polynomial Regression)

Đây là bước quan trọng nhất để giải quyết bài toán "Truth or Bluff". Chúng ta sử dụng mô hình `lin_reg_2` (đã huấn luyện với bậc 4) để dự đoán.

## Logic thực hiện

Khác với hồi quy tuyến tính đơn giản, mô hình đa thức không thể nhận đầu vào thô là `[[6.5]]`.

- **Lý do:** Mô hình được huấn luyện trên ma trận đặc trưng bao gồm các lũy thừa ($x_1, x_1^2, x_1^3, x_1^4$).
    
- **Giải pháp:** Giá trị đầu vào `6.5` cũng phải đi qua bước biến đổi `poly_reg.fit_transform` tương tự như dữ liệu huấn luyện để tạo ra các đặc trưng lũy thừa tương ứng.
    

## Mã nguồn (Python)

python

`# Dự đoán mức lương cho Level 6.5 bằng mô hình Polynomial Regression # Bước 1: Biến đổi giá trị 6.5 thành các đặc trưng đa thức # Bước 2: Đưa vào hàm predict của lin_reg_2 lin_reg_2.predict(poly_reg.fit_transform([[6.5]]))`

## Kết quả và So sánh

|Mô hình|Giá trị dự đoán|So với yêu cầu ($160k)|Đánh giá|
|---|---|---|---|
|**Linear Regression**|~$330,000|Sai lệch rất lớn (+170k)|**Không phù hợp**|
|**Polynomial Regression**|**~$158,862**|Rất sát (-1.2k)|**Chính xác**|

## Kết luận bài toán (Verdict)

- Ứng viên yêu cầu **$160,000**.
    
- Mô hình dự đoán mức lương thực tế tại vị trí đó là xấp xỉ **$159,000**.
    
- **Kết luận:** Ứng viên **trung thực** (Truth). Công ty có thể tự tin tuyển dụng ứng viên này vì mức lương yêu cầu là hợp lý và đúng sự thật.
    

---

## Tổng kết bài học Hồi quy Đa thức

Qua bài thực hành này, chúng ta đã đạt được các mục tiêu:

1. Hiểu được giới hạn của **Hồi quy Tuyến tính** trên dữ liệu phi tuyến.
    
2. Biết cách xây dựng mô hình **Hồi quy Đa thức** bằng cách tạo ma trận đặc trưng lũy thừa (`PolynomialFeatures`).
    
3. Biết cách trực quan hóa dữ liệu và làm mượt đường cong dự đoán.
    
4. Biết cách dự đoán giá trị đơn lẻ (single prediction) với dữ liệu đầu vào cần qua xử lý (transform).
    

**Bước tiếp theo:**  
Trong các phần sau của khóa học, chúng ta sẽ tìm hiểu các mô hình hồi quy phi tuyến mạnh mẽ khác như **SVR (Support Vector Regression)** để so sánh hiệu quả trên cùng tập dữ liệu này.