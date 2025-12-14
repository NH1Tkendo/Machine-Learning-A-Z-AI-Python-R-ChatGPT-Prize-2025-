## Giới thiệu về Non-linear SVR

## Bối cảnh

- Trong bài trước, chúng ta đã tìm hiểu về trực giác của **Linear SVR** (Hồi quy Vector hỗ trợ tuyến tính). Đây là bước khởi đầu đơn giản.
    
- Tuy nhiên, thế giới thực tế của SVR rộng lớn hơn nhiều với các mô hình phi tuyến tính (**Non-linear SVR**).
    
- Các mô hình này mạnh mẽ hơn nhờ sử dụng các kỹ thuật như **Kernel RBF** (Radial Basis Function) và **Thủ thuật Kernel** (Kernel Trick).
    

## Sự khác biệt trong bài thực hành sắp tới

- **Cảnh báo quan trọng**: Trong bài thực hành Python ngay sau đây, chúng ta sẽ xây dựng một mô hình SVR đầu tiên.
    
- Mô hình này sẽ là **Non-linear SVR** (phi tuyến tính), không phải là đường thẳng đơn giản như lý thuyết vừa học.
    
- Lý do: Bài thực hành sẽ hướng dẫn sử dụng `RBF Kernel`.
    
- Kết quả trực quan: Đường hồi quy sẽ là đường cong phức tạp, không phải đường thẳng. Để hiểu bản chất, ta cần hình dung việc ánh xạ dữ liệu lên không gian 3 chiều (3D), tính toán và chiếu ngược lại.
    

## Lộ trình học tập lý thuyết SVR Phi tuyến tính

Lý thuyết chi tiết về Non-linear SVR được sắp xếp ở phần sau của khóa học (trong phần Phân loại - Classification) để đảm bảo tính sư phạm. Dưới đây là các chủ đề kiến thức nền tảng cần có để hiểu sâu về nó:

1. **SVM Intuition**: Trực giác về máy vector hỗ trợ.
    
2. **Kernel SVM Intuition**: Trực giác về Kernel SVM.
    
3. **Mapping to a higher dimension**: Ánh xạ lên không gian chiều cao hơn.
    
4. **The Kernel Trick**: Thủ thuật Kernel.
    
5. **Types of Kernel functions**: Các loại hàm Kernel.
    
6. **Non-linear Kernel SVR**: Tổng hợp lại cho bài toán hồi quy.
    

## Lựa chọn phương pháp học tập

Do sự lệch pha giữa thời điểm thực hành (ngay bây giờ) và thời điểm học lý thuyết sâu (sau này), giảng viên đưa ra 2 lựa chọn:

## Lựa chọn 1: Thực hành trước (Khuyên dùng)

- Tiếp tục học ngay các bài thực hành Python về SVR của Hadelin.
    
- **Lưu ý tâm thế**: Chấp nhận rằng chúng ta đang sử dụng một `Non-linear Kernel` mà chưa cần hiểu sâu về toán học bên dưới ngay lập tức.
    
- Lý thuyết chi tiết sẽ được giải thích cặn kẽ khi đến phần **Kernel SVM** sau này.
    

## Lựa chọn 2: Học lý thuyết trước

- Tạm dừng phần này.
    
- Chuyển sang phần **Classification**, tìm học các bài về **Kernel SVM** (như danh sách lộ trình phía trên).
    
- Sau khi nắm vững lý thuyết và các khái niệm như Kernel Trick, quay lại đây để làm bài thực hành Python.