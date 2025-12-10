## Mã hóa dữ liệu phân loại (Encoding Categorical Data)

Mã hóa dữ liệu phân loại là một bước quan trọng trong tiền xử lý dữ liệu cho machine learning, giúp chuyển đổi các biến dạng văn bản (như tên quốc gia, màu sắc) thành định dạng số mà mô hình có thể xử lý được.datacamp+1​

## Vấn đề với mã hóa số thông thường

Khi làm việc với dữ liệu phân loại (ví dụ: cột Country chứa France, Spain, Germany), việc đơn giản mã hóa thành 0, 1, 2 sẽ gây ra vấn đề:

- Mô hình machine learning có thể hiểu nhầm rằng có một **thứ tự số học** giữa các giá trị (France < Spain < Germany)
    
- Điều này dẫn đến việc diễn giải sai mối tương quan giữa đặc trưng và biến mục tiêu
    
- Thực tế, giữa các quốc gia không có quan hệ thứ tự nào cả
    

## One Hot Encoding là gì?

One Hot Encoding là phương pháp mã hóa tốt hơn, hoạt động như sau:[datacamp](https://www.datacamp.com/tutorial/one-hot-encoding-python-tutorial)​

- Chuyển một cột phân loại thành **nhiều cột nhị phân**
    
- Số cột mới = số lượng danh mục khác nhau trong cột gốc
    
- Mỗi danh mục được biểu diễn bằng một **vector nhị phân** (chỉ chứa 0 và 1)
    

**Ví dụ cụ thể:**

- France → `[1, 0, 0]`
    
- Spain → `[0, 1, 0]`
    
- Germany → `[0, 0, 1]`
    

Kết quả là cột Country ban đầu sẽ được thay thế bằng 3 cột mới chứa các giá trị 0 và 1, loại bỏ hoàn toàn thứ tự số học giữa các quốc gia.

## Xử lý biến phụ thuộc nhị phân

Đối với cột biến phụ thuộc (dependent variable) như "Purchased" với giá trị Yes/No:

- Có thể đơn giản thay thế bằng 0 và 1
    
- Điều này **hoàn toàn chấp nhận được** với biến kết quả nhị phân
    
- Không ảnh hưởng đến độ chính xác của mô hình
    

## Triển khai với Python và Scikit-learn

Để thực hiện One Hot Encoding, cần import 2 class từ thư viện scikit-learn:

python

`from sklearn.compose import ColumnTransformer from sklearn.preprocessing import OneHotEncoder`

**Giải thích:**

- `ColumnTransformer`: class từ module `compose`, dùng để áp dụng các phép biến đổi khác nhau cho các cột khác nhau[dev](https://dev.to/vikas_gulia/columntransformer-and-pipelines-in-scikit-learn-clean-scalable-and-powerful-preprocessing-3mff)​
    
- `OneHotEncoder`: class từ module `preprocessing`, thực hiện mã hóa one-hot[scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)​
    

Bước tiếp theo sẽ kết hợp 2 class này để mã hóa cột Country trong tập dữ liệu.

1. [https://www.datacamp.com/tutorial/one-hot-encoding-python-tutorial](https://www.datacamp.com/tutorial/one-hot-encoding-python-tutorial)
2. [https://machinelearningmastery.com/one-hot-encoding-understanding-the-hot-in-data/](https://machinelearningmastery.com/one-hot-encoding-understanding-the-hot-in-data/)
3. [https://dev.to/vikas_gulia/columntransformer-and-pipelines-in-scikit-learn-clean-scalable-and-powerful-preprocessing-3mff](https://dev.to/vikas_gulia/columntransformer-and-pipelines-in-scikit-learn-clean-scalable-and-powerful-preprocessing-3mff)
4. [https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)
5. [https://www.geeksforgeeks.org/machine-learning/ml-one-hot-encoding/](https://www.geeksforgeeks.org/machine-learning/ml-one-hot-encoding/)
6. [https://www.blog.trainindata.com/one-hot-encoding-categorical-variables/](https://www.blog.trainindata.com/one-hot-encoding-categorical-variables/)
7. [https://developers.google.com/machine-learning/crash-course/categorical-data/one-hot-encoding](https://developers.google.com/machine-learning/crash-course/categorical-data/one-hot-encoding)
8. [https://stackoverflow.com/questions/55217933/scikit-learn-columntransformer-onehotencoder](https://stackoverflow.com/questions/55217933/scikit-learn-columntransformer-onehotencoder)
9. [https://www.shiksha.com/online-courses/articles/handling-categorical-variables-with-one-hot-encoding/](https://www.shiksha.com/online-courses/articles/handling-categorical-variables-with-one-hot-encoding/)
10. [https://github.com/scikit-learn/scikit-learn/discussions/27830](https://github.com/scikit-learn/scikit-learn/discussions/27830)