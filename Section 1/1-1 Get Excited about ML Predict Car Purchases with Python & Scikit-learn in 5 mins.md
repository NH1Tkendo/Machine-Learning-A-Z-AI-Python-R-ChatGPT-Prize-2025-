## Giới thiệu về Sức mạnh của Machine Learning

Bài học này giới thiệu nhanh về quy trình xây dựng một mô hình học máy (Machine Learning) đơn giản trong vòng dưới 5 phút, thông qua bài toán phân loại thực tế.

## Tình huống giả định (Scenario)

Bạn là một nhà khoa học dữ liệu (Data Scientist) làm việc cho một công ty xe hơi. Nhiệm vụ của bạn là xác định khách hàng tiềm năng cho chiến dịch bán hàng sắp tới.

- **Mục tiêu:** Dự đoán khách hàng nào có khả năng mua xe cao nhất.
    
- **Dữ liệu đầu vào:** Tuổi (Age) và Mức lương ước tính (Estimated Salary) của khách hàng.
    
- **Dữ liệu huấn luyện:** Dữ liệu từ một chiến dịch tương tự trước đó, bao gồm thông tin khách hàng và nhãn cho biết họ đã mua xe hay chưa.
    

## Công cụ và Mô hình

- **Mô hình:** Hồi quy Logistic (Logistic Regression).[studocu](https://www.studocu.vn/vn/document/truong-dai-hoc-bach-khoa-ha-noi/bai-tap-on-tap/chuan-hoa-du-lieu-feature-scaling/125490320)​youtube​
    
- **Môi trường:** Google Colab.
    
- **Ngôn ngữ:** Python.
    

## Quy trình thực hiện (Workflow)

Các bước chính được thực hiện trong đoạn mã mẫu:

1. **Tải dữ liệu (Load Datasets):** Nhập dữ liệu lịch sử và dữ liệu dự án mới.
    
2. **Nhập thư viện (Import Libraries):** Khai báo các thư viện cần thiết để xử lý dữ liệu.
    
3. **Trực quan hóa dữ liệu (Data Visualization):**
    
    - Vẽ biểu đồ phân tán (scatter plot) để quan sát mối quan hệ giữa Tuổi và Lương.
        
    - **Kết quả quan sát:** Khách hàng mua xe (chấm xanh) thường có độ tuổi hoặc mức lương cao hơn so với nhóm không mua (chấm đỏ).
        
4. **Chuẩn hóa dữ liệu (Feature Scaling):**[fmit](https://fmit.vn/en/glossary/feature-scaling-la-gi)​
    
    - Đây là bước quan trọng để đưa các đặc trưng về cùng một thang đo, giúp thuật toán hoạt động hiệu quả hơn.
        
5. **Huấn luyện mô hình (Model Training):**
    
    - Xây dựng mô hình Hồi quy Logistic (Logistic Regression) dựa trên dữ liệu lịch sử.
        
6. **Trực quan hóa kết quả mô hình:**
    
    - Biểu đồ hiển thị một "đường ranh giới" phân chia hai vùng.
        
    - **Vùng trên đường ranh giới:** Dự đoán sẽ mua xe.
        
    - **Vùng dưới đường ranh giới:** Dự đoán sẽ không mua.
        
    - _Lưu ý:_ Sẽ có một số điểm dữ liệu bị phân loại sai (mismatches), đây là điều bình thường vì không có mô hình nào hoàn hảo tuyệt đối.
        

## Ứng dụng thực tế

Sau khi mô hình được huấn luyện, áp dụng nó vào tập dữ liệu mới (New Project Data) để đưa ra dự đoán:

- **Kết quả:** Xác định được nhóm khách hàng nằm trong "vùng xanh" (có khả năng mua cao).
    
- **Giá trị doanh nghiệp:** Bộ phận Marketing có thể chỉ tập trung vào nhóm khách hàng này, giúp tiết kiệm chi phí và tối ưu hóa lợi nhuận đầu tư (ROI).
    

## Ghi chú thêm

Bài thực hành này là một cách tiếp cận đơn giản hóa (simplified approach) để minh họa nhanh sức mạnh của Machine Learning. Trong thực tế, quy trình sẽ cần thêm các bước chuyên sâu như:

- Chia tập dữ liệu thành tập huấn luyện và tập kiểm tra (Training set & Test set).
    
- Xây dựng ma trận nhầm lẫn (Confusion Matrix).
    
- Tính toán các chỉ số độ chính xác (Accuracy ratios).
    

1. [https://www.studocu.vn/vn/document/truong-dai-hoc-bach-khoa-ha-noi/bai-tap-on-tap/chuan-hoa-du-lieu-feature-scaling/125490320](https://www.studocu.vn/vn/document/truong-dai-hoc-bach-khoa-ha-noi/bai-tap-on-tap/chuan-hoa-du-lieu-feature-scaling/125490320)
2. [https://www.youtube.com/watch?v=2iAHBhHpfcQ](https://www.youtube.com/watch?v=2iAHBhHpfcQ)
3. [https://fmit.vn/en/glossary/feature-scaling-la-gi](https://fmit.vn/en/glossary/feature-scaling-la-gi)
4. [https://www.reddit.com/r/MLQuestions/comments/llh4y3/noob_question_what_exactly_does_feature_scaling/](https://www.reddit.com/r/MLQuestions/comments/llh4y3/noob_question_what_exactly_does_feature_scaling/)
5. [https://machinelearningcoban.com/general/2017/02/06/featureengineering/](https://machinelearningcoban.com/general/2017/02/06/featureengineering/)
6. [https://www.linkedin.com/pulse/feature-scaling-machine-learning-what-why-matters-how-andrade-e8jbf](https://www.linkedin.com/pulse/feature-scaling-machine-learning-what-why-matters-how-andrade-e8jbf)
7. [https://arxiv.org/html/2501.08621v1](https://arxiv.org/html/2501.08621v1)
8. [https://www.facebook.com/groups/genzlamit/posts/9530626616985867/](https://www.facebook.com/groups/genzlamit/posts/9530626616985867/)
9. [https://www.facebook.com/groups/machinelearningcoban/posts/1274487999675271/](https://www.facebook.com/groups/machinelearningcoban/posts/1274487999675271/)
10. [https://www.studocu.vn/vn/document/truong-dai-hoc-khoa-hoc-tu-nhien-dai-hoc-quoc-gia-ha-noi/toan-vat-li/text-classification-jjjjjjjj/99400927](https://www.studocu.vn/vn/document/truong-dai-hoc-khoa-hoc-tu-nhien-dai-hoc-quoc-gia-ha-noi/toan-vat-li/text-classification-jjjjjjjj/99400927)
11. [https://ieeexplore.ieee.org/iel8/6287639/10380310/10714325.pdf](https://ieeexplore.ieee.org/iel8/6287639/10380310/10714325.pdf)
12. [https://www.facebook.com/aivietnam.edu.vn/posts/slide-b%C3%A0i-gi%E1%BA%A3ng-v%E1%BB%81-logistic-regression-140-trang-logistic-regression-l%C3%A0-n%E1%BB%81n-t%E1%BA%A3ng/896011049308281/](https://www.facebook.com/aivietnam.edu.vn/posts/slide-b%C3%A0i-gi%E1%BA%A3ng-v%E1%BB%81-logistic-regression-140-trang-logistic-regression-l%C3%A0-n%E1%BB%81n-t%E1%BA%A3ng/896011049308281/)
13. [https://www.linkedin.com/pulse/feature-scaling-different-methods-machine-learning-part-kumar-g-r-3thvc](https://www.linkedin.com/pulse/feature-scaling-different-methods-machine-learning-part-kumar-g-r-3thvc)
14. [https://tanvietco.vn/the-final-word-information-to-logistic-regression/](https://tanvietco.vn/the-final-word-information-to-logistic-regression/)
15. [https://eprints.uet.vnu.edu.vn/eprints/id/eprint/3350/1/SMT_Grammatical%20error%20correction_Report_Nguyen_Tuan_Vinh-2018%20(1).pdf](https://eprints.uet.vnu.edu.vn/eprints/id/eprint/3350/1/SMT_Grammatical%20error%20correction_Report_Nguyen_Tuan_Vinh-2018%20\(1\).pdf)
16. [https://vjs.ac.vn/jcc/article/view/13233](https://vjs.ac.vn/jcc/article/view/13233)
17. [https://tuyendung.vti.com.vn/en-US/Blog/BlogDetail/276](https://tuyendung.vti.com.vn/en-US/Blog/BlogDetail/276)
18. [https://journals.sagepub.com/doi/10.3233/JIFS-172053](https://journals.sagepub.com/doi/10.3233/JIFS-172053)