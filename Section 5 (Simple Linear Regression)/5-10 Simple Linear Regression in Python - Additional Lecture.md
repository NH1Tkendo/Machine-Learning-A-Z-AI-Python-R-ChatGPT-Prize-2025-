## Mở rộng: Hai câu hỏi thường gặp trong Hồi quy tuyến tính

Trong thực tế, sau khi xây dựng mô hình, chúng ta thường cần thực hiện hai tác vụ cụ thể mà không phải lúc nào cũng được đề cập trong quy trình cơ bản: dự đoán cho một giá trị đơn lẻ và trích xuất phương trình toán học cuối cùng.

## 1. Dự đoán cho một giá trị đơn lẻ

**Câu hỏi:** Làm thế nào để sử dụng mô hình đã huấn luyện để dự đoán mức lương cho một nhân viên cụ thể có **12 năm kinh nghiệm**?

**Cách thực hiện:**  
Sử dụng phương thức `predict` tương tự như khi dự đoán trên tập kiểm tra, nhưng thay vì truyền vào cả một mảng dữ liệu, ta truyền vào giá trị cụ thể cần dự đoán.

**Mã nguồn (Python):**

python

`# Dự đoán lương cho nhân viên có 12 năm kinh nghiệm print(regressor.predict([[12]]))`

**Lưu ý quan trọng:**

- Phương thức `predict` luôn yêu cầu đầu vào là một **mảng 2 chiều (2D array)**.
    
- Do đó, giá trị `12` phải được đặt trong hai cặp ngoặc vuông `[[12]]`.
    
    - `[12]` → Mảng 1 chiều (1D vector) → _Sẽ báo lỗi nếu dùng trực tiếp._
        
    - `[[12]]` → Mảng 2 chiều (2D array) → _Định dạng đúng._
        

## 2. Trích xuất phương trình hồi quy cuối cùng

**Câu hỏi:** Làm thế nào để lấy được các hệ số b0b_0b0 và b1b_1b1 để viết thành phương trình hoàn chỉnh y=b0+b1xy = b_0 + b_1xy=b0+b1x?

**Cách thực hiện:**  
Truy cập trực tiếp vào các thuộc tính (attributes) của đối tượng `regressor` sau khi đã huấn luyện.

- **Hệ số góc (b1b_1b1)**: Thuộc tính `coef_`
    
- **Hệ số chặn (b0b_0b0)**: Thuộc tính `intercept_`
    

**Mã nguồn (Python):**

python

`# Lấy hệ số góc (b1) và hệ số chặn (b0) print(regressor.coef_) print(regressor.intercept_)`

**Kết quả ví dụ (Giả định):**  
Nếu kết quả trả về là `coef_ = [9312]` và `intercept_ = 26780`, phương trình hồi quy tuyến tính cuối cùng sẽ là:

Salary=26780+9312×YearsExperience\text{Salary} = 26780 + 9312 \times \text{YearsExperience}Salary=26780+9312×YearsExperience

**(Dịch: Lương = 26,780 + 9,312 × Số năm kinh nghiệm)**

---

_Nguồn tham khảo chi tiết và code mẫu có thể xem tại file Colab tặng kèm của khóa học: [SuperDataScience Bonus](https://www.superdatascience.com/pages/ml-regression-bonus-1)_