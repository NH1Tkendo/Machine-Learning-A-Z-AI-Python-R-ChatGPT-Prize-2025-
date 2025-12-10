## Mã hóa nhãn (Label Encoding) cho biến phụ thuộc

Sau khi xử lý xong biến độc lập (cột Country), bước tiếp theo là mã hóa biến phụ thuộc (cột Purchased) chứa các giá trị văn bản "Yes" và "No" thành dạng số để mô hình có thể xử lý.[vitalflux](https://vitalflux.com/labelencoder-example-single-multiple-columns/)​[youtube](https://www.youtube.com/watch?v=XkDRBr1yHLQ)​

## Tại sao dùng Label Encoder cho biến phụ thuộc?

- **Đặc điểm dữ liệu**: Cột Purchased là biến nhị phân (chỉ có 2 giá trị Yes/No), không yêu cầu tạo nhiều cột mới như One Hot Encoding.
    
- **Tính phù hợp**: Label Encoding chuyển đổi trực tiếp thành các số nguyên (ví dụ: No=0, Yes=1), rất phù hợp cho biến mục tiêu (y) trong các bài toán phân loại.qualitypointtech+1​
    
- **Hiệu quả**: Không làm tăng số chiều dữ liệu, giữ nguyên cấu trúc vector đơn của biến mục tiêu.[dev](https://dev.to/engrmark/when-to-use-labelencoder-and-onehotencoder-in-machine-learning-7gl)​
    

## Quy trình thực hiện với Scikit-learn

Chúng ta sử dụng class `LabelEncoder` từ module `sklearn.preprocessing`.

## 1. Import thư viện

python

`from sklearn.preprocessing import LabelEncoder`

## 2. Khởi tạo đối tượng

python

`le = LabelEncoder()`

_Lưu ý: Khác với `ColumnTransformer`, `LabelEncoder` không cần tham số đầu vào khi khởi tạo vì nó chỉ làm việc với một vector duy nhất._

## 3. Thực hiện biến đổi

Sử dụng phương thức `fit_transform` để vừa học các nhãn (No/Yes) vừa chuyển đổi chúng thành số (0/1) trong cùng một bước.

python

`y = le.fit_transform(y)`

## 4. Kết quả

Sau khi chạy, vector `y` sẽ chứa các giá trị số thay vì chuỗi ký tự:

- "No" → 0
    
- "Yes" → 1
    

Thứ tự mã hóa phụ thuộc vào thứ tự bảng chữ cái (alphabetical order) của các chuỗi ký tự đầu vào.[qualitypointtech](https://www.blog.qualitypointtech.com/2025/09/labelencoder-vs-onehotencoder.html)​

## Tổng kết công cụ tiền xử lý

Đến đây, bạn đã hoàn thành việc mã hóa dữ liệu phân loại với 2 công cụ quan trọng:

1. **One Hot Encoding** (với `ColumnTransformer`): Dùng cho biến độc lập (features) có nhiều hơn 2 danh mục không có thứ tự (ví dụ: quốc gia).
    
2. **Label Encoding** (với `LabelEncoder`): Dùng cho biến phụ thuộc (target variable) hoặc biến phân loại nhị phân.
    

Bước tiếp theo trong quy trình sẽ là chia tập dữ liệu thành tập huấn luyện (training set) và tập kiểm tra (test set).

1. [https://vitalflux.com/labelencoder-example-single-multiple-columns/](https://vitalflux.com/labelencoder-example-single-multiple-columns/)
2. [https://www.youtube.com/watch?v=XkDRBr1yHLQ](https://www.youtube.com/watch?v=XkDRBr1yHLQ)
3. [https://www.blog.qualitypointtech.com/2025/09/labelencoder-vs-onehotencoder.html](https://www.blog.qualitypointtech.com/2025/09/labelencoder-vs-onehotencoder.html)
4. [https://dev.to/engrmark/when-to-use-labelencoder-and-onehotencoder-in-machine-learning-7gl](https://dev.to/engrmark/when-to-use-labelencoder-and-onehotencoder-in-machine-learning-7gl)
5. [https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)
6. [https://scikit-learn.org/0.17/modules/generated/sklearn.preprocessing.LabelEncoder.html](https://scikit-learn.org/0.17/modules/generated/sklearn.preprocessing.LabelEncoder.html)
7. [https://stackoverflow.com/questions/41773751/working-of-labelencoder-in-sklearn](https://stackoverflow.com/questions/41773751/working-of-labelencoder-in-sklearn)
8. [https://stackoverflow.com/questions/24458645/label-encoding-across-multiple-columns-in-scikit-learn](https://stackoverflow.com/questions/24458645/label-encoding-across-multiple-columns-in-scikit-learn)
9. [https://codefinity.com/courses/v2/a65bbc96-309e-4df9-a790-a1eb8c815a1c/1fce4aa9-710f-4bc9-ad66-16b4b2d30929/2d9a6807-ea36-4430-8cc5-2f1231fe6f81](https://codefinity.com/courses/v2/a65bbc96-309e-4df9-a790-a1eb8c815a1c/1fce4aa9-710f-4bc9-ad66-16b4b2d30929/2d9a6807-ea36-4430-8cc5-2f1231fe6f81)
10. [https://www.geeksforgeeks.org/machine-learning/ml-label-encoding-of-datasets-in-python/](https://www.geeksforgeeks.org/machine-learning/ml-label-encoding-of-datasets-in-python/)
11. [https://stackoverflow.com/questions/50473381/scikit-learns-labelbinarizer-vs-onehotencoder](https://stackoverflow.com/questions/50473381/scikit-learns-labelbinarizer-vs-onehotencoder)
12. [https://www.geeksforgeeks.org/machine-learning/sklearnlabelencoder-with-never-seen-before-values/](https://www.geeksforgeeks.org/machine-learning/sklearnlabelencoder-with-never-seen-before-values/)
13. [https://www.upgrad.com/blog/label-encoder-vs-one-hot-encoder/](https://www.upgrad.com/blog/label-encoder-vs-one-hot-encoder/)
14. [https://www.geeksforgeeks.org/machine-learning/one-hot-encoding-vs-label-encoding/](https://www.geeksforgeeks.org/machine-learning/one-hot-encoding-vs-label-encoding/)
15. [https://sklearn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html](https://sklearn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)
16. [https://www.kaggle.com/questions-and-answers/391391](https://www.kaggle.com/questions-and-answers/391391)
17. [https://drlee.io/a-comprehensive-guide-to-categorical-data-encoding-exploring-labelencoder-and-onehotencoder-and-4ecd0f68ac66](https://drlee.io/a-comprehensive-guide-to-categorical-data-encoding-exploring-labelencoder-and-onehotencoder-and-4ecd0f68ac66)
18. [https://www.youtube.com/watch?v=mHkdcA-zyYE](https://www.youtube.com/watch?v=mHkdcA-zyYE)
19. [https://stackoverflow.com/questions/73271013/difference-between-one-hot-encoding-and-label-encoding-of-target-output-label](https://stackoverflow.com/questions/73271013/difference-between-one-hot-encoding-and-label-encoding-of-target-output-label)
20. [https://www.statology.org/label-encoding-vs-one-hot-encoding/](https://www.statology.org/label-encoding-vs-one-hot-encoding/)