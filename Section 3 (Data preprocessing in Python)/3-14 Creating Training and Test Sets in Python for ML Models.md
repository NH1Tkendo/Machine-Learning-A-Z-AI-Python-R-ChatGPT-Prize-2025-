## Chia tập dữ liệu (Splitting Data)

Đây là bước cuối cùng trong quy trình tiền xử lý dữ liệu trước khi chuẩn hóa. Mục tiêu là chia dữ liệu thành 4 tập con để phục vụ huấn luyện và kiểm thử mô hình.

## Công cụ sử dụng

- **Thư viện**: `scikit-learn` (thư viện phổ biến nhất cho machine learning trong Python)
    
- **Module**: `model_selection`
    
- **Hàm**: `train_test_split`educative+1​
    

## Quy trình thực hiện

## 1. Import hàm cần thiết

python

`from sklearn.model_selection import train_test_split`

## 2. Xác định các biến đầu ra

Hàm `train_test_split` sẽ trả về 4 biến theo đúng thứ tự sau:[csdn](https://blog.csdn.net/weixin_37226516/article/details/60873949)​

1. `X_train`: Ma trận đặc trưng dùng để huấn luyện.
    
2. `X_test`: Ma trận đặc trưng dùng để kiểm thử (chứa các quan sát mới).
    
3. `y_train`: Biến mục tiêu tương ứng với `X_train`.
    
4. `y_test`: Biến mục tiêu tương ứng với `X_test`.
    

## 3. Cấu hình và gọi hàm

python

`X_train, X_test, y_train, y_test = train_test_split(     X, y,    test_size=0.2,    random_state=1 )`

**Giải thích các tham số:**

- `X`, `y`: Ma trận đặc trưng và vector biến mục tiêu cần chia.[youtube](https://www.youtube.com/watch?v=6Kmujmnqsvo)​
    
- `test_size=0.2`: Tỉ lệ chia dữ liệu.
    
    - 20% dữ liệu sẽ vào tập kiểm thử (`X_test`, `y_test`).
        
    - 80% dữ liệu sẽ vào tập huấn luyện (`X_train`, `y_train`).
        
    - Đây là tỉ lệ khuyến nghị phổ biến, đảm bảo đủ dữ liệu để mô hình học (8 mẫu) nhưng vẫn có đủ dữ liệu mới để đánh giá (2 mẫu).[leadpages](https://www.leadpages.com/blog/sklearn-train-test-split)​[youtube](https://www.youtube.com/watch?v=6Kmujmnqsvo)​
        
- `random_state=1`: Kiểm soát tính ngẫu nhiên.scikit-learn+1​
    
    - Thiết lập một giá trị cố định (ví dụ `1`) giúp đảm bảo kết quả chia giống nhau mỗi lần chạy code.
        
    - Điều này rất quan trọng cho mục đích giảng dạy và tái lập kết quả thực nghiệm.
        

## Kết quả mong đợi

- Tập huấn luyện (`X_train`, `y_train`) sẽ chứa phần lớn dữ liệu để mô hình học các mối tương quan.
    
- Tập kiểm thử (`X_test`, `y_test`) sẽ chứa dữ liệu "mới" để đánh giá hiệu năng mô hình sau khi học.
    

Sau khi hoàn thành bước này, dữ liệu đã sẵn sàng cho bước cuối cùng là **Feature Scaling** (Chuẩn hóa dữ liệu).

1. [https://www.educative.io/answers/what-is-the-traintestsplit-function-in-sklearn](https://www.educative.io/answers/what-is-the-traintestsplit-function-in-sklearn)
2. [https://eitca.org/artificial-intelligence/eitc-ai-gcml-google-cloud-machine-learning/advancing-in-machine-learning/scikit-learn/examination-review-scikit-learn/how-can-the-train_test_split-function-in-scikit-learn-be-used-to-create-training-and-test-data/](https://eitca.org/artificial-intelligence/eitc-ai-gcml-google-cloud-machine-learning/advancing-in-machine-learning/scikit-learn/examination-review-scikit-learn/how-can-the-train_test_split-function-in-scikit-learn-be-used-to-create-training-and-test-data/)
3. [https://blog.csdn.net/weixin_37226516/article/details/60873949](https://blog.csdn.net/weixin_37226516/article/details/60873949)
4. [https://www.youtube.com/watch?v=6Kmujmnqsvo](https://www.youtube.com/watch?v=6Kmujmnqsvo)
5. [https://www.leadpages.com/blog/sklearn-train-test-split](https://www.leadpages.com/blog/sklearn-train-test-split)
6. [https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)
7. [https://www.geeksforgeeks.org/machine-learning/what-is-scikit-learn-random-state-in-splitting-dataset/](https://www.geeksforgeeks.org/machine-learning/what-is-scikit-learn-random-state-in-splitting-dataset/)
8. [https://stackoverflow.com/questions/49147774/what-is-random-state-in-sklearn-model-selection-train-test-split-example](https://stackoverflow.com/questions/49147774/what-is-random-state-in-sklearn-model-selection-train-test-split-example)
9. [https://stackoverflow.com/questions/42191717/scikit-learn-random-state-in-splitting-dataset](https://stackoverflow.com/questions/42191717/scikit-learn-random-state-in-splitting-dataset)
10. [https://stackoverflow.com/questions/48065601/python-sklearn-train-test-split-how-to-set-which-data-is-taken-for-training](https://stackoverflow.com/questions/48065601/python-sklearn-train-test-split-how-to-set-which-data-is-taken-for-training)
11. [https://www.geeksforgeeks.org/machine-learning/how-to-do-train-test-split-using-sklearn-in-python/](https://www.geeksforgeeks.org/machine-learning/how-to-do-train-test-split-using-sklearn-in-python/)
12. [https://realpython.com/train-test-split-python-data/](https://realpython.com/train-test-split-python-data/)
13. [https://scikit-learn.org/0.19/modules/generated/sklearn.model_selection.train_test_split.html](https://scikit-learn.org/0.19/modules/generated/sklearn.model_selection.train_test_split.html)
14. [https://www.youtube.com/watch?v=_tex9QxBX-U](https://www.youtube.com/watch?v=_tex9QxBX-U)
15. [https://www.reddit.com/r/programminghelp/comments/12kkko3/what_does_random_state_do_in_train_test_split_in/](https://www.reddit.com/r/programminghelp/comments/12kkko3/what_does_random_state_do_in_train_test_split_in/)
16. [https://www.reddit.com/r/learnprogramming/comments/f88cel/enquires_about_sklearnmodel_selectiontrain_test/](https://www.reddit.com/r/learnprogramming/comments/f88cel/enquires_about_sklearnmodel_selectiontrain_test/)
17. [https://stackoverflow.com/questions/57754373/train-test-split-method-of-scikit-learn](https://stackoverflow.com/questions/57754373/train-test-split-method-of-scikit-learn)
18. [https://blog.naver.com/PostView.naver?blogId=siniphia&logNo=221396370872](https://blog.naver.com/PostView.naver?blogId=siniphia&logNo=221396370872)
19. [https://hye0archive.tistory.com/8](https://hye0archive.tistory.com/8)
20. [https://www.youtube.com/watch?v=KYM2a5p2CsY](https://www.youtube.com/watch?v=KYM2a5p2CsY)