## Trực quan hóa SVR (Độ phân giải cao)

## Mục đích và Thách thức

- **Mục đích**: Vẽ đường hồi quy mượt mà (smooth curve) thay vì các đoạn thẳng nối nhau, giúp nhìn rõ hơn mối quan hệ phi tuyến tính.
    
- **Thách thức**: Do mô hình SVR được huấn luyện trên dữ liệu đã quy chuẩn (scaled), việc tạo lưới dữ liệu (`X_grid`) và dự đoán trên lưới này đòi hỏi phải chuyển đổi qua lại liên tục giữa **thang đo gốc** và **thang đo đã quy chuẩn**.
    

## Quy trình xử lý Logic

Để vẽ biểu đồ chính xác, ta cần tuân thủ quy trình nghiêm ngặt sau:

1. **Tạo lưới dữ liệu (`X_grid`)**:
    
    - Cần lấy giá trị Min và Max từ dữ liệu gốc ($X$ thực tế).
        
    - Do biến `X` hiện tại đang lưu giá trị đã quy chuẩn, ta phải dùng `sc_X.inverse_transform(X)` để lấy lại giá trị gốc trước khi tạo lưới.
        
2. **Vẽ điểm dữ liệu thực (Scatter Plot)**:
    
    - Tương tự bài trước, cần `inverse_transform` cả `X` và `y` để hiển thị chấm đỏ ở toạ độ thực tế.
        
3. **Dự đoán trên lưới (Prediction Line)**:
    
    - `X_grid` được tạo ra đang ở thang đo gốc (ví dụ: 1.0, 1.1, 1.2...).
        
    - **Quan trọng**: Mô hình SVR (`regressor`) chỉ hiểu dữ liệu đã quy chuẩn.
        
    - $\rightarrow$ **Bước 1**: Phải `transform` `X_grid` bằng `sc_X` trước khi đưa vào hàm `.predict()`.
        
    - $\rightarrow$ **Bước 2**: Kết quả dự đoán trả về là lương đã quy chuẩn. Phải `inverse_transform` kết quả này bằng `sc_y` để vẽ được lên biểu đồ thực tế.
        

## Mã nguồn thực hiện

python

`# 1. Tạo lưới dữ liệu X_grid (Mật độ 0.1) # Cần nghịch đảo X để lấy giới hạn thực tế (Level 1 đến 10) X_grid = np.arange(min(sc_X.inverse_transform(X)), max(sc_X.inverse_transform(X)), 0.1) X_grid = X_grid.reshape((len(X_grid), 1)) # 2. Vẽ biểu đồ phân tán các điểm dữ liệu thực (Màu đỏ) plt.scatter(sc_X.inverse_transform(X), sc_y.inverse_transform(y), color = 'red') # 3. Vẽ đường dự đoán SVR (Màu xanh) # Logic lồng ghép: # - Input: sc_X.transform(X_grid) -> Đưa lưới về dạng scaled để model hiểu # - Predict: regressor.predict(...) -> Dự đoán (kết quả dạng scaled) # - Output: sc_y.inverse_transform(...) -> Đưa kết quả về lương thực tế (USD) plt.plot(X_grid, sc_y.inverse_transform(regressor.predict(sc_X.transform(X_grid)).reshape(-1, 1)), color = 'blue') plt.title('Truth or Bluff (SVR)') plt.xlabel('Position level') plt.ylabel('Salary') plt.show()`

## Kết quả

- Biểu đồ hiển thị một đường cong trơn tru (smooth curve) màu xanh.
    
- Đường cong này bám sát các điểm dữ liệu tốt hơn nhiều so với các mô hình tuyến tính, thể hiện sức mạnh của **Kernel RBF** trong SVR.