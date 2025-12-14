## Giới thiệu về Support Vector Regression (SVR)

## Lịch sử và Nguồn gốc

- **Support Vector Regression (SVR)** được phát minh vào những năm 90 bởi **Vladimir Vapnik** và các đồng nghiệp tại Bell Labs (nay là Nokia Bell Labs).
    
- Các lý thuyết nền tảng về **Support Vector Machine (SVM)** và SVR được thảo luận trong cuốn sách _"The Nature of Statistical Learning"_ (1992) của Vladimir Vapnik.
    
- Trong khóa học này, nội dung sẽ bao gồm cả phân loại (Classification) và hồi quy (Regression), cũng như các khái niệm nâng cao như **Kernel SVM**, **Kernel SVR** và **Thủ thuật Kernel (Kernel Trick)**.
    

## So sánh: Linear Regression vs. SVR

Để hiểu rõ bản chất của SVR, ta cần so sánh nó với mô hình Hồi quy tuyến tính đơn giản (Simple Linear Regression).

## 1. Hồi quy tuyến tính đơn giản (Simple Linear Regression)

- **Phương pháp:** Sử dụng **Bình phương tối thiểu thông thường (Ordinary Least Squares - OLS)**.
    
- **Mục tiêu:** Tìm ra đường thẳng sao cho sai số giữa giá trị thực tế ($y$) và giá trị dự đoán ($\hat{y}$) là nhỏ nhất.
    
- **Cơ chế:** Cố gắng giảm thiểu sai số cho **tất cả** các điểm dữ liệu trong tập huấn luyện.
    
- **Công thức (Ý tưởng):** Giảm thiểu tổng bình phương sai số: $\sum (y - \hat{y})^2$.
    

## 2. Support Vector Regression (SVR)

![[support_vector_regression.png]]

Khác với đường thẳng đơn lẻ trong OLS, SVR sử dụng khái niệm một "đường ống" (tube).

## Cấu trúc "Ống không nhạy cảm với Epsilon" ($\epsilon$-Insensitive Tube)

- SVR tạo ra một đường hồi quy ở giữa và một vùng bao quanh gọi là **$\epsilon$-Insensitive Tube**.
    
- **Độ rộng ống ($\epsilon$):** Được đo theo phương thẳng đứng (dọc theo trục y).
    
- **Nguyên lý hoạt động:**
    
    - **Điểm nằm TRONG ống:** Sai số được bỏ qua hoàn toàn. Mô hình coi các điểm này là dự đoán chính xác hoặc nằm trong biên độ sai số chấp nhận được.
        
    - **Điểm nằm NGOÀI ống:** Sai số được tính toán và quan tâm. Khoảng cách được đo từ điểm đó đến **mép của ống** (chứ không phải đường trung tâm).
        

## Biến bù (Slack Variables)

Các điểm nằm ngoài ống có khoảng cách đến ống được gọi là **biến bù (Slack variables)**, ký hiệu là $\xi$ (xi).

- $\xi^*$: Khoảng cách cho các điểm nằm dưới ống.
    
- $\xi$: Khoảng cách cho các điểm nằm trên ống.
    

## Mục tiêu tối ưu hóa

- SVR không cố gắng giảm thiểu sai số của tất cả các điểm.
    
- Nó cho phép một vùng đệm linh hoạt ($\epsilon$) nơi sai số không được tính.
    
- Mục tiêu là giảm thiểu tổng khoảng cách của các điểm **nằm ngoài** ống ($\xi$ và $\xi^*$) đồng thời tối ưu hóa các hệ số của mô hình.
    

## Tại sao gọi là "Support Vector"?

- Mọi điểm dữ liệu trên đồ thị đều có thể coi là một vector.
    
- **Support Vectors (Vector hỗ trợ):** Là những điểm dữ liệu nằm **bên ngoài** ống $\epsilon$-Insensitive Tube.
    
- **Vai trò:** Chỉ những điểm này mới ảnh hưởng đến việc xây dựng và định vị mô hình (ống). Chúng "hỗ trợ" (support) cấu trúc hoặc sự hình thành của ống.
    
- Các điểm nằm bên trong ống bị bỏ qua và không ảnh hưởng đến thuật toán.
    

## Tài liệu tham khảo thêm

Nếu muốn tìm hiểu sâu hơn về lý thuyết toán học:

- **Sách:** _"Efficient Learning Machines: Theories, Concepts, and Applications for Engineers and System Design"_ của Mariette Awad và Rahul Khanna.
    
- **Chương:** 4 (Support Vector Regression).
    
- **Lưu ý:** Một số tài liệu có thể định nghĩa Support Vector hơi khác nhau (ví dụ: bao gồm cả các điểm nằm trên biên), nhưng cách giải thích phổ biến là các điểm nằm ngoài ống đóng vai trò quyết định cấu trúc mô hình.