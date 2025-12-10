## Triển khai One Hot Encoding với ColumnTransformer

Bước này tập trung vào việc áp dụng mã hóa One Hot cho cột "Country" trong khi giữ nguyên các cột số liệu khác (Age, Salary).

## 1. Cấu trúc của `ColumnTransformer`

Để thực hiện biến đổi dữ liệu trên các cột cụ thể, chúng ta khởi tạo đối tượng `ColumnTransformer` với hai tham số chính:

- `transformers`: Danh sách các biến đổi cần thực hiện. Mỗi biến đổi là một tuple gồm 3 phần tử:
    
    - **Tên biến đổi**: Chuỗi ký tự đặt tên cho bước này (ví dụ: `'encoder'`).
        
    - **Class biến đổi**: Đối tượng thực hiện biến đổi (ví dụ: `OneHotEncoder()`).
        
    - **Cột áp dụng**: Danh sách chỉ số (index) hoặc tên cột cần biến đổi (ví dụ: `[0]` cho cột Country).
        
- `remainder`: Xác định cách xử lý các cột không được biến đổi.
    
    - `'passthrough'`: Giữ lại các cột không biến đổi (quan trọng để giữ Age và Salary).
        
    - Mặc định là `'drop'` (sẽ xóa các cột không được liệt kê trong `transformers`).
        

python

`import numpy as np from sklearn.compose import ColumnTransformer from sklearn.preprocessing import OneHotEncoder # Cấu hình ColumnTransformer ct = ColumnTransformer(     transformers=[('encoder', OneHotEncoder(), [0])],    remainder='passthrough' )`

## 2. Thực hiện biến đổi (Fit và Transform)

Thay vì thực hiện hai bước riêng lẻ (`fit` rồi `transform`), chúng ta sử dụng phương thức `fit_transform` để tối ưu hóa quy trình.

- **Đầu vào**: Ma trận đặc trưng `X`.
    
- **Đầu ra**: Ma trận mới đã được mã hóa One Hot (cột Country được thay thế bằng 3 cột nhị phân).
    

python

`# Áp dụng biến đổi và cập nhật ma trận X X = np.array(ct.fit_transform(X))`

## 3. Lưu ý quan trọng về định dạng đầu ra

Kết quả trả về từ `fit_transform` của `ColumnTransformer` không phải lúc nào cũng là NumPy array (có thể là sparse matrix).

- **Yêu cầu của Scikit-learn**: Các mô hình machine learning thường yêu cầu đầu vào là NumPy array.
    
- **Giải pháp**: Bắt buộc chuyển đổi kết quả về dạng NumPy array bằng `np.array()` để đảm bảo tính tương thích cho các bước huấn luyện sau này.
    

## Tóm tắt mã nguồn hoàn chỉnh

python

`import numpy as np from sklearn.compose import ColumnTransformer from sklearn.preprocessing import OneHotEncoder # Giả sử X là ma trận đặc trưng đầu vào # [0] là chỉ số cột Country cần mã hóa ct = ColumnTransformer(     transformers=[('encoder', OneHotEncoder(), [0])],    remainder='passthrough' ) # Biến đổi và ép kiểu về numpy array X = np.array(ct.fit_transform(X))`

1. [https://scikit-learn.org/stable/modules/generated/sklearn.compose.ColumnTransformer.html](https://scikit-learn.org/stable/modules/generated/sklearn.compose.ColumnTransformer.html)
2. [https://stackoverflow.com/questions/70933014/how-to-use-columntransformer-to-return-a-dataframe](https://stackoverflow.com/questions/70933014/how-to-use-columntransformer-to-return-a-dataframe)
3. [https://scikit-learn.org/1.8/auto_examples/compose/plot_column_transformer_mixed_types.html](https://scikit-learn.org/1.8/auto_examples/compose/plot_column_transformer_mixed_types.html)
4. [https://scikit-learn.org/stable/modules/generated/sklearn.compose.make_column_transformer.html](https://scikit-learn.org/stable/modules/generated/sklearn.compose.make_column_transformer.html)
5. [https://apxml.com/courses/getting-started-with-scikit-learn/chapter-6-building-pipelines/columntransformer-pipelines](https://apxml.com/courses/getting-started-with-scikit-learn/chapter-6-building-pipelines/columntransformer-pipelines)
6. [https://sklearn.org/1.6/modules/generated/sklearn.compose.ColumnTransformer.html](https://sklearn.org/1.6/modules/generated/sklearn.compose.ColumnTransformer.html)
7. [https://www.pythontutorials.net/blog/how-to-use-sklearn-fit-transform-with-pandas-and-return-dataframe-instead-of-numpy-array/](https://www.pythontutorials.net/blog/how-to-use-sklearn-fit-transform-with-pandas-and-return-dataframe-instead-of-numpy-array/)
8. [https://www.geeksforgeeks.org/machine-learning/using-columntransformer-in-scikit-learn-for-data-preprocessing/](https://www.geeksforgeeks.org/machine-learning/using-columntransformer-in-scikit-learn-for-data-preprocessing/)
9. [https://github.com/scikit-learn/scikit-learn/issues/18372](https://github.com/scikit-learn/scikit-learn/issues/18372)
10. [https://stackoverflow.com/questions/35723472/how-to-use-sklearn-fit-transform-with-pandas-and-return-dataframe-instead-of-num](https://stackoverflow.com/questions/35723472/how-to-use-sklearn-fit-transform-with-pandas-and-return-dataframe-instead-of-num)
11. [https://docs.huihoo.com/scikit-learn/0.20/modules/generated/sklearn.compose.ColumnTransformer.html](https://docs.huihoo.com/scikit-learn/0.20/modules/generated/sklearn.compose.ColumnTransformer.html)
12. [https://dsyemen.github.io/scikit-learn/modules/generated/sklearn.compose.ColumnTransformer.html](https://dsyemen.github.io/scikit-learn/modules/generated/sklearn.compose.ColumnTransformer.html)
13. [https://github.com/scikit-learn/scikit-learn/discussions/22297](https://github.com/scikit-learn/scikit-learn/discussions/22297)
14. [https://github.com/scikit-learn/scikit-learn/blob/master/sklearn/compose/tests/test_column_transformer.py](https://github.com/scikit-learn/scikit-learn/blob/master/sklearn/compose/tests/test_column_transformer.py)
15. [https://stackoverflow.com/questions/66287100/can-you-passthrough-a-specific-column-in-a-scikit-learn-columntransformer](https://stackoverflow.com/questions/66287100/can-you-passthrough-a-specific-column-in-a-scikit-learn-columntransformer)
16. [https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.FunctionTransformer.html](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.FunctionTransformer.html)
17. [https://www.sktime.net/en/latest/api_reference/auto_generated/sktime.transformations.panel.compose.ColumnTransformer.html](https://www.sktime.net/en/latest/api_reference/auto_generated/sktime.transformations.panel.compose.ColumnTransformer.html)
18. [https://stackoverflow.com/questions/72517139/columntransformer-remainder-passthrough-gives-me-error](https://stackoverflow.com/questions/72517139/columntransformer-remainder-passthrough-gives-me-error)
19. [https://ubc-cs.github.io/cpsc330-2024W2/lectures/notes/06_column-transformer-text-feats.html](https://ubc-cs.github.io/cpsc330-2024W2/lectures/notes/06_column-transformer-text-feats.html)
20. [https://www.kaggle.com/code/ksvmuralidhar/columntransformer-pipeline-simplified](https://www.kaggle.com/code/ksvmuralidhar/columntransformer-pipeline-simplified)