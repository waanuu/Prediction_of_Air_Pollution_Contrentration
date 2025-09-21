# 🌍 Dự đoán Nồng độ Ô Nhiễm Không Khí  

## 🚀 Giới thiệu  
Ô nhiễm không khí là vấn đề nghiêm trọng, ảnh hưởng trực tiếp đến sức khỏe con người.  
Nghiên cứu này tập trung vào việc **dự đoán nồng độ các chất ô nhiễm (CO, NOx, NO₂)** dựa trên dữ liệu đo đạc thực tế, với mục tiêu:  

- Hỗ trợ giám sát môi trường.  
- Đưa ra cảnh báo sớm.  
- Hỗ trợ hoạch định chính sách bảo vệ sức khỏe cộng đồng.  

---

## 🎯 Mục tiêu  
- Tiền xử lý dữ liệu môi trường (xử lý thiếu, ngoại lai, chuẩn hóa, giảm chiều).  
- Xây dựng mô hình học máy để dự đoán nồng độ các chất ô nhiễm.  
- So sánh và đánh giá hiệu suất giữa các mô hình khác nhau.  

---

## 📂 Dữ liệu  
- **Nguồn:** [UCI Machine Learning Repository – Air Quality Dataset (De Vito, 2008)](https://doi.org/10.24432/C59K5F)  
- **Thời gian thu thập:** 3–4/2004, tại Lucca (Ý).  
- **Kích thước:** ~9358 bản ghi (mỗi giờ), 15 thuộc tính.  
- **Các thông số chính:** CO, NOx, NO₂, nhiệt độ, độ ẩm, áp suất, phản ứng cảm biến,…  
- **Đặc điểm:** Dữ liệu thiếu được mã hóa bằng `-200`.  

---

## ⚙️ Các bước thực hiện  

### 1. Tiền xử lý dữ liệu  
- **Xử lý giá trị thiếu:** Mean, Median, Forward Fill, Interpolation, KNN → chọn **Interpolation**.  
- **Chuẩn hóa:** StandardScaler (Z-score).  
- **Xử lý ngoại lai:** IQR, Z-score linh hoạt, Isolation Forest.  
- **Giảm chiều dữ liệu:** Mutual Information + Permutation Importance.  

### 2. Xây dựng mô hình  
- **Random Forest + Rolling Forecast**  
  - Dự báo CO, NOx, NO₂ trong 7 ngày tới.  
  - Kết quả tốt cho CO, độ chính xác giảm dần với NO₂.  

- **Hồi quy tuyến tính**  
  - Hiệu quả với CO, NOx.  
  - Với NO₂, mô hình làm mượt quá mức, kém hiệu quả hơn.  

### 3. Đánh giá  
- **Chỉ số:** RMSE, MAE.  
- **Trực quan hóa:** Biểu đồ so sánh giá trị thực và dự đoán.  

---

## 📈 Kết quả  
- **CO(GT):** Sai số < 10%, dự đoán sát với thực tế.  
- **NOx(GT):** Bám xu hướng, nhưng nhạy kém với biến động mạnh.  
- **NO₂(GT):** Mô hình làm mượt quá, không phản ứng tốt với dao động nhanh.  
- **Kết luận:** Tiền xử lý đóng vai trò quan trọng trong cải thiện hiệu suất mô hình.  

---

## 🔮 Hướng phát triển  
- Kết hợp thêm yếu tố ngoại sinh (thời tiết, giao thông, sự kiện).  
- Thử nghiệm mô hình tiên tiến hơn: **ARIMA, LSTM, Transformer**.  
- Xây dựng hệ thống dự báo và cảnh báo theo thời gian thực.  

---

## 🛠️ Công nghệ sử dụng  
- Python (`pandas`, `numpy`, `matplotlib`, `scikit-learn`)  
- Random Forest, Linear Regression  
- Rolling Forecast  
- Isolation Forest, KNN, Interpolation  
