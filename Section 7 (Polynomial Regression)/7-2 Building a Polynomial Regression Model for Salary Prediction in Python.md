## Thực hành Hồi quy Đa thức: Bài toán "Sự thật hay Nói dối" (Truth or Bluff)

Bài học này hướng dẫn xây dựng một mô hình **Hồi quy phi tuyến (Non-linear Regression)** để xử lý tập dữ liệu có mối quan hệ phi tuyến tính, nơi mà mô hình Hồi quy tuyến tính đa biến (Multiple Linear Regression) không còn phù hợp.

## Tài nguyên chuẩn bị

- **File Python:** `polynomial_regression.ipynb` (chạy trên Google Colab hoặc Jupyter Notebook).
    
- **Tập dữ liệu:** `Position_Salaries.csv`.
    

## Kịch bản bài toán (Scenario)

Bạn đóng vai bộ phận nhân sự (HR) đang tuyển dụng một ứng viên tiềm năng.

- **Tình huống:** Ứng viên yêu cầu mức lương **$160,000/năm**.
    
- **Lý do:** Ứng viên khẳng định đây là mức thu nhập cũ tại công ty trước đó.
    
- **Nhiệm vụ:** Xác định xem ứng viên đang nói thật hay nói dối (bluffing) bằng cách dự đoán mức lương thực tế dựa trên dữ liệu công khai.
    

## Phân tích dữ liệu (Dataset Analysis)

Dữ liệu thu thập được từ các trang web công khai (ví dụ: Glassdoor) liệt kê mức lương theo từng vị trí tại công ty cũ của ứng viên:

- Dữ liệu bao gồm các cấp bậc từ Nhân viên phân tích kinh doanh (Business Analyst) đến Giám đốc điều hành (CEO).
    
- Mối quan hệ giữa Cấp bậc (Position Level) và Lương (Salary) là **phi tuyến tính** (non-linear).
    

## Logic xử lý bài toán

1. **Xác định vị trí:**
    
    - Theo LinkedIn, ứng viên giữ chức vụ **Region Manager** (tương ứng với **Level 6** trong tập dữ liệu).
        
    - Mức lương tham chiếu cho Level 6 là $150,000 và Level 7 (Partner) là $200,000.
        
2. **Nội suy dữ liệu (Extrapolation):**
    
    - Ứng viên đã làm việc ở vị trí Region Manager được 2 năm, nghĩa là trình độ thực tế nằm giữa Level 6 và Level 7.
        
    - Ta sẽ đặt cấp bậc của ứng viên là **6.5**.
        
3. **Mục tiêu mô hình:**
    
    - Huấn luyện mô hình **Hồi quy Đa thức (Polynomial Regression)** trên tập dữ liệu `Position_Salaries`.
        
    - Dự đoán mức lương chính xác cho `Level = 6.5`.
        
    - So sánh kết quả dự đoán với con số $160,000 để đưa ra kết luận tuyển dụng.