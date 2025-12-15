## Tổng quan về Cây Quyết định (Decision Trees)

Trong học máy (Machine Learning), thuật ngữ **CART** là viết tắt của _Cây phân loại và hồi quy (Classification and Regression Trees)_. Đây là thuật ngữ bao trùm hai loại cây quyết định:

1. **Cây phân loại (Classification Trees)**
    
2. **Cây hồi quy (Regression Trees)**
    

**Lưu ý:** Phần này tập trung vào **Cây hồi quy**. Loại này phức tạp hơn so với cây phân loại và yêu cầu sự chú ý chi tiết hơn về mặt toán học và tư duy.

## Cấu trúc dữ liệu và Trực quan hóa

Để hiểu cách thuật toán hoạt động, ta xét một tập dữ liệu được biểu diễn trên biểu đồ phân tán (scatterplot):

- **Biến độc lập (Independent variables):** Có hai biến là $X_1$ và $X_2$.
    
- **Biến phụ thuộc (Dependent variable):** Là biến $Y$ mà chúng ta cần dự đoán.
    

## Mối quan hệ không gian

- Trên biểu đồ 2D, chúng ta chỉ nhìn thấy vị trí của các điểm dựa trên $X_1$ và $X_2$.
    
- Biến $Y$ thực chất là **chiều thứ 3** (hình dung như trục vuông góc đi ra từ màn hình).
    
- **Chiến lược:** Thuật toán sẽ làm việc với mặt phẳng $X_1, X_2$ để xây dựng cây trước, sau đó mới quay lại xử lý giá trị $Y$.
    

## Cơ chế hoạt động của Thuật toán

Thuật toán Cây hồi quy hoạt động bằng cách chia nhỏ biểu đồ phân tán thành các đoạn (segments).

## 1. Quy trình phân chia (Splitting)

Thuật toán sẽ tạo ra các đường cắt (splits) để chia dữ liệu thành các vùng khác nhau dựa trên các điều kiện của biến độc lập.

- **Ví dụ:**
    
    - Cắt tại $X_1 \approx 20$: Chia dữ liệu thành 2 phần ($< 20$ và $> 20$).
        
    - Tiếp tục cắt phần bên phải tại $X_2 \approx 170$.
        
    - Tiếp tục cắt nhỏ hơn nữa...
        

## 2. Tiêu chuẩn phân chia

Cách thức và vị trí thực hiện các vết cắt được xác định bởi thuật toán dựa trên khái niệm **Entropi thông tin (Information Entropy)**.

- Thuật toán kiểm tra xem việc phân chia có làm tăng lượng thông tin hữu ích về các điểm dữ liệu hay không.
    
- **Điểm dừng (Stopping criteria):**
    
    - Khi không thể thêm thông tin giá trị vào nhóm.
        
    - Khi số lượng điểm dữ liệu trong một nút lá nhỏ hơn một tỷ lệ nhất định (ví dụ: ít hơn 5% tổng số điểm).
        

Các phân đoạn cuối cùng được gọi là **Lá cuối cùng (Terminal Leaves)**.

## Xây dựng Cây Quyết định (Decision Tree)

Từ các vết cắt trên biểu đồ, ta xây dựng sơ đồ cây tương ứng với các luồng câu hỏi **Có/Không (Yes/No)**.

![[DecisionTree-Condition.png]]
**Ví dụ quy trình:**

1. **Split 1:** Kiểm tra $X_1 < 20$?
    
    - Nếu _Có_ $\rightarrow$ Đi về nhánh trái.
        
    - Nếu _Không_ $\rightarrow$ Đi về nhánh phải $\rightarrow$ Sang Split 2.
        
2. **Split 2:** Kiểm tra $X_2 < 170$?
    
    - Tiếp tục phân nhánh...
        
3. **Split 3 & 4:** Các điều kiện kiểm tra tiếp theo như $X_2 < 200$ hoặc $X_1 < 40$.
    

Mục đích là phân loại bất kỳ điểm dữ liệu mới nào vào đúng "Lá cuối cùng" (Terminal leaf) tương ứng.

## Cách dự đoán giá trị $Y$ (Cốt lõi của Regression Tree)

Sau khi cây đã được xây dựng và chia thành các lá, làm thế nào để dự đoán giá trị $Y$ cho một điểm dữ liệu mới?

## Nguyên lý Trung bình (Averaging)

Giá trị dự đoán được tính bằng **giá trị trung bình (average)** của biến $Y$ của tất cả các điểm dữ liệu nằm trong lá đó.

1. **Bước 1:** Xác định điểm mới rơi vào lá nào dựa trên $X_1, X_2$.
    
2. **Bước 2:** Lấy trung bình cộng của tất cả các giá trị $Y$ đã có sẵn trong lá đó.
    
3. **Bước 3:** Gán giá trị trung bình đó làm kết quả dự đoán.
    

## Ví dụ minh họa

Giả sử ta có điểm dữ liệu mới với $X_1 = 30, X_2 = 50$:

- Dựa vào cây, điểm này rơi vào một lá cụ thể.
    
- Trong lá đó, thuật toán tính trung bình $Y$ của các điểm cũ là $-64.1$.
    
- $\rightarrow$ Giá trị dự đoán cho điểm mới là $Y = -64.1$.
    

## Tại sao phương pháp này hiệu quả?

- Nếu không dùng Cây hồi quy: Ta chỉ có thể lấy trung bình $Y$ của _toàn bộ_ tập dữ liệu, dẫn đến độ chính xác thấp.
    
- Khi dùng Cây hồi quy: Tập dữ liệu được chia nhỏ thành các vùng có đặc tính tương đồng, giúp giá trị trung bình cục bộ (local average) phản ánh chính xác hơn giá trị thực tế.
    

---

**Tổng kết:** Cây hồi quy thay thế việc tính toán phức tạp bằng cách phân nhóm dữ liệu và gán giá trị trung bình của nhóm đó cho các quan sát mới.