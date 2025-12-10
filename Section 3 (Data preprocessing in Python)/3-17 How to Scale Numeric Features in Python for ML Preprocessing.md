## Thực hành Chuẩn hóa dữ liệu với Scikit-learn

## Khởi tạo công cụ

Sử dụng thư viện `scikit-learn` để thực hiện kỹ thuật **Standardization** (Chuẩn hóa Z-score).

**Các bước thực hiện:**

1. Import class `StandardScaler` từ module `preprocessing`.
    
2. Tạo một đối tượng (object) từ class này. Không cần truyền tham số đầu vào vì công cụ sẽ tự động tính toán giá trị trung bình và độ lệch chuẩn.
    

python

`from sklearn.preprocessing import StandardScaler # Tạo đối tượng scaler sc = StandardScaler()`

## Xử lý biến giả (Dummy Variables)

Một câu hỏi phổ biến trong cộng đồng khoa học dữ liệu: **Có nên áp dụng Feature Scaling cho các biến giả (Dummy Variables) không?**

👉 **Câu trả lời: KHÔNG.**

**Lý do:**

- **Phạm vi giá trị đã phù hợp**: Mục tiêu của chuẩn hóa là đưa giá trị về khoảng [-3, +3]. Các biến giả (giá trị 0 hoặc 1) đã nằm trong phạm vi này, nên không cần biến đổi thêm.
    
- **Mất tính giải thích (Interpretability)**:
    
    - Biến giả đại diện cho định danh (ví dụ: 1 là Pháp, 0 là Tây Ban Nha).
        
    - Nếu chuẩn hóa, các số 0 và 1 sẽ biến thành các số thập phân vô nghĩa, làm mất khả năng xác định biến đó đại diện cho quốc gia nào.
        
- **Hiệu suất mô hình**: Việc chuẩn hóa biến giả không cải thiện đáng kể độ chính xác của mô hình huấn luyện.
    

**Kết luận:**

- Chỉ áp dụng Feature Scaling cho các **biến số thực (numerical variables)** có sự chênh lệch lớn về độ lớn (ví dụ: Tuổi từ 0-100, Lương từ 0-100.000).
    
- Giữ nguyên các cột biến giả để bảo toàn thông tin định danh.