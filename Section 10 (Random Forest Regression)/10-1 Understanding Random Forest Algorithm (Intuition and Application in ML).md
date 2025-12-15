## Hồi quy Rừng ngẫu nhiên (Random Forest Regression)

## Khái niệm

**Rừng ngẫu nhiên (Random Forest)** là một phiên bản của phương pháp **Học kết hợp (Ensemble Learning)** – tương tự như _Tăng cường độ dốc (Gradient Boosting)_.

- **Học kết hợp (Ensemble Learning)**: Là kỹ thuật sử dụng nhiều thuật toán (hoặc cùng một thuật toán nhiều lần) và kết hợp chúng lại để tạo ra một mô hình mạnh mẽ hơn nhiều so với bản gốc.
    
- Trong bài này, kỹ thuật được áp dụng cho **Cây hồi quy (Regression Trees)** thay vì phân loại.
    

## Quy trình thực hiện thuật toán

Quá trình xây dựng và dự đoán của Random Forest Regression diễn ra theo 4 bước chính:

1. **Chọn dữ liệu**: Chọn ngẫu nhiên $K$ điểm dữ liệu từ tập huấn luyện (Training set).
    
2. **Xây dựng cây**: Xây dựng một **Cây quyết định (Decision Tree)** chỉ dựa trên $K$ điểm dữ liệu đã chọn (thay vì toàn bộ dữ liệu).
    
3. **Lặp lại**: Chọn số lượng cây muốn xây dựng (ví dụ: `Ntree = 500`) và lặp lại bước 1 và 2 để tạo ra nhiều cây khác nhau.
    
4. **Dự đoán**:
    
    - Với một điểm dữ liệu mới, đưa điểm đó vào tất cả các cây trong rừng để mỗi cây đưa ra một giá trị dự đoán $y$.
        
    - Giá trị dự đoán cuối cùng được tính bằng **trung bình cộng** của tất cả các giá trị $y$ được dự đoán bởi các cây thành phần.
        

Công thức tính giá trị dự đoán cuối cùng:

$y_{final} = \frac{y_1 + y_2 + ... + y_n}{n}$

_(Trong đó $y_n$ là dự đoán của cây thứ $n$ và $n$ là tổng số cây trong rừng)_

## Ưu điểm của Random Forest

- **Độ chính xác cao hơn**: Việc lấy trung bình của nhiều dự đoán giúp loại bỏ sai số. Ngay cả khi một cây riêng lẻ hoạt động không tốt do cách chọn dữ liệu ngẫu nhiên, việc kết hợp hàng trăm cây sẽ đưa kết quả về gần giá trị đúng nhất.
    
- **Tính ổn định (Stability)**: Các thuật toán _Ensemble_ ổn định hơn. Những thay đổi nhỏ trong tập dữ liệu có thể ảnh hưởng lớn đến một cây quyết định đơn lẻ, nhưng rất khó để ảnh hưởng đến cả một rừng cây.
    

## Ví dụ trực quan: Trò chơi đoán số lượng (The Marble/Balloon Jar Game)

Để hiểu về trực giác của thuật toán, hãy hình dung trò chơi đoán số lượng viên kẹo (hoặc bóng bay) trong một cái lọ lớn tại hội chợ:

- **Cách tiếp cận đơn lẻ**: Bạn tự nhìn và đưa ra một con số dự đoán. Khả năng sai số rất cao.
    
- **Cách tiếp cận Ensemble (Rừng ngẫu nhiên)**:
    
    1. Bạn không đoán ngay.
        
    2. Bạn đứng quan sát và ghi lại câu trả lời của hàng trăm người chơi khác.
        
    3. Sau khi thu thập đủ dữ liệu (ví dụ: 100 - 500 người), bạn tính **trung bình cộng** (hoặc trung vị để loại bỏ các giá trị ngoại lai) của tất cả các dự đoán đó.
        

**Kết luận**: Về mặt thống kê, trung bình cộng của đám đông thường tuân theo **phân phối chuẩn (Normal Distribution)** và có xu hướng nằm rất gần với đáp án chính xác hơn bất kỳ dự đoán cá nhân nào. Đây chính là sức mạnh của việc kết hợp nhiều mô hình dự đoán.