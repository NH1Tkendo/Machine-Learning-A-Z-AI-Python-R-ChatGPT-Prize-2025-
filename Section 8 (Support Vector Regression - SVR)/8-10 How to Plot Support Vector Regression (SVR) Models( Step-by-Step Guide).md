## Trực quan hóa kết quả SVR (Visualization)

## Vấn đề với dữ liệu đã quy chuẩn

Khi vẽ biểu đồ, chúng ta muốn hiển thị **giá trị thực tế** (Level từ 1-10, Lương từ 45k-1M) để dễ hiểu, thay vì hiển thị các giá trị đã quy chuẩn (nằm trong khoảng -1 đến 3).  
Do đó, ta cần sử dụng phương thức `inverse_transform` để nghịch đảo quy chuẩn cho cả trục $X$ và trục $y$.

## Các bước thực hiện trong Code

Chúng ta có thể tái sử dụng đoạn mã từ bài Hồi quy đa thức (Polynomial Regression) và điều chỉnh lại:

1. **Biểu đồ phân tán (Scatter Plot - Dữ liệu thực):**
    
    - Trục hoành ($X$): Cần nghịch đảo về Level gốc $\rightarrow$ `sc_X.inverse_transform(X)`.
        
    - Trục tung ($y$): Cần nghịch đảo về Lương gốc $\rightarrow$ `sc_y.inverse_transform(y)`.
        
2. **Đường hồi quy (Regression Line - Dự đoán):**
    
    - Trục hoành ($X$): Vẫn nghịch đảo về Level gốc.
        
    - Trục tung (Dự đoán):
        
        - Hàm `predict` cần đầu vào là $X$ **đã quy chuẩn** (biến `X` hiện tại đã thỏa mãn điều này, không cần transform lại).
            
        - Kết quả trả về của `predict` là lương **đã quy chuẩn**, nên cần `inverse_transform` bằng `sc_y`.
            
        - Cần `reshape(-1, 1)` để tránh lỗi định dạng mảng.
            

## Mã nguồn chi tiết

python

`# Vẽ các điểm dữ liệu thực tế (Màu đỏ) # Cần inverse_transform cả X và y để về thang đo gốc plt.scatter(sc_X.inverse_transform(X), sc_y.inverse_transform(y), color = 'red') # Vẽ đường dự đoán của mô hình SVR (Màu xanh) # X đầu vào cho predict giữ nguyên là scaled X # Kết quả predict cần được reshape và inverse_transform bằng sc_y plt.plot(sc_X.inverse_transform(X),           sc_y.inverse_transform(regressor.predict(X).reshape(-1, 1)),         color = 'blue') plt.title('Truth or Bluff (SVR)') plt.xlabel('Position level') plt.ylabel('Salary') plt.show()`

## Nhận xét kết quả

- **Đường cong SVR**: Đường màu xanh bám sát các điểm dữ liệu màu đỏ tốt hơn nhiều so với hồi quy tuyến tính.
    
- **Ngoại lệ (Outlier)**: Điểm dữ liệu cuối cùng (CEO - Level 10) có thể không nằm hoàn toàn trên đường dự đoán. Đây là đặc tính của SVR khi cố gắng tối ưu hóa biên độ sai số (tube), coi điểm cuối cùng quá xa biệt lập là nhiễu hoặc ngoại lệ.