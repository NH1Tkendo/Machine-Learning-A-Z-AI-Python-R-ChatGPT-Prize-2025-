## Dự đoán kết quả mới (Predicting a New Result)

Mục tiêu là dự đoán mức lương cho vị trí cấp bậc **6.5**. Chúng ta sẽ thực hiện dự đoán với cả hai mô hình để so sánh.

## 1. Dự đoán bằng Hồi quy Tuyến tính (Linear Regression)

Sử dụng đối tượng `lin_reg` đã huấn luyện để dự đoán.

**Cú pháp quan trọng:**  
Hàm `predict()` yêu cầu đầu vào là một mảng 2 chiều (2D array), ngay cả khi chỉ dự đoán cho một giá trị duy nhất.

- Trong Python, mảng 2 chiều được biểu diễn bằng cặp ngoặc vuông lồng nhau `[[ ]]`.
    
- `[[6.5]]` đại diện cho một mảng có 1 hàng và 1 cột, chứa giá trị 6.5.
    

**Mã nguồn:**

python

`# Dự đoán mức lương cho Level 6.5 bằng mô hình Linear Regression lin_reg.predict([[6.5]])`

**Kết quả:**

- Giá trị trả về: Khoảng **$330,000**.
    
- **Đánh giá:** Con số này quá cao so với mức lương thực tế xung quanh cấp bậc 6 (150k) và 7 (200k).
    
- **Kết luận:** Mô hình tuyến tính đưa ra dự đoán sai lệch lớn (như đã thấy trên biểu đồ, đường thẳng nằm rất xa các điểm dữ liệu ở đoạn giữa). Nếu dùng con số này để đàm phán, nhà tuyển dụng sẽ bị thiệt hại nặng.
    

## 2. Định dạng mảng 2 chiều (Giải thích thêm)

- `[6.5]`: Vector 1 chiều (List/Vector).
    
- `[[6.5]]`: Mảng 2 chiều (Matrix/Array) - Đây là định dạng bắt buộc của `scikit-learn` cho phương thức `predict`.
    
    - Cặp ngoặc ngoài cùng: Xác định các hàng (rows).
        
    - Cặp ngoặc bên trong: Xác định các cột (columns).
        
    - Ví dụ: `[[6.5, 5], [2, 3]]` sẽ tạo ra ma trận 2x2.
        

---

_Phần tiếp theo sẽ hướng dẫn dự đoán bằng mô hình Hồi quy Đa thức để xem liệu kết quả có sát với con số $160,000 mà ứng viên đưa ra hay không._