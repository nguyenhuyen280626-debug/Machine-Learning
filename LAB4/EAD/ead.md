# Dự đoán Giá Nhà

## 1. Tổng quan về bộ dữ liệu (Dataset Overview)

* Đọc bộ dữ liệu (`london_houses.csv`).
* Hiển thị 5 dòng đầu tiên của bộ dữ liệu.
* Kiểm tra số lượng bản ghi và số lượng đặc trưng.
* Xác định kiểu dữ liệu của tất cả các đặc trưng.
* Thực hiện thống kê mô tả cho bộ dữ liệu.
* Xác định biến mục tiêu (Giá nhà).

---

## 2. Phân tích dữ liệu thiếu (Missing Value Analysis)

* Phát hiện các giá trị bị thiếu.
* Tính tỷ lệ phần trăm dữ liệu bị thiếu.
* Phân tích quy luật xuất hiện của dữ liệu thiếu.
* Quyết định loại bỏ hoặc thay thế các giá trị bị thiếu.

---

## 3. Phân tích đơn biến (Univariate Analysis)

### Đặc trưng số (Numerical Features)

* Phân tích phân phối dữ liệu.
* Trực quan hóa bằng biểu đồ Histogram.
* Phân tích độ lệch phân phối (Skewness).
* Thống kê mô tả.
* Trực quan hóa bằng biểu đồ mật độ (Density Plot).

### Đặc trưng phân loại (Categorical Features)

* Bảng tần suất.
* Phân bố của từng nhóm dữ liệu.
* Trực quan hóa bằng biểu đồ cột (Bar Chart).
* Phân tích sự mất cân bằng giữa các nhóm dữ liệu.

---

## 4. Phân tích hai biến và đa biến (Bivariate and Multivariate Analysis)

### Biến số với biến số (Numerical vs Numerical)

* Ma trận tương quan (Correlation Matrix).
* Bản đồ nhiệt (Heatmap).
* Biểu đồ phân tán (Scatter Plot).
* Phân tích mối quan hệ giữa các đặc trưng số và giá nhà.

### Biến phân loại với biến số (Categorical vs Numerical)

* Thống kê theo từng nhóm.
* Giá nhà trung bình theo từng nhóm.
* Trực quan hóa bằng biểu đồ Boxplot.

### Biến phân loại với biến phân loại (Categorical vs Categorical)

* Bảng liên hợp (Contingency Table).
* Phân tích bảng chéo (Crosstab).
* Kiểm định Chi-Square (nếu cần).

---

## 5. Phát hiện giá trị ngoại lệ (Outlier Detection)

* Phương pháp khoảng tứ phân vị (Interquartile Range - IQR).
* Trực quan hóa bằng biểu đồ Boxplot.
* Phát hiện các giá trị ngoại lệ.
* Quyết định có nên loại bỏ các giá trị ngoại lệ hay không.

---
# Kết quả mong đợi (Expected Insights)

Sau khi hoàn thành quá trình Khám phá dữ liệu (Exploratory Data Analysis - EDA), dự kiến thu được các kết quả sau:

* Hiểu được cấu trúc tổng thể của bộ dữ liệu.
* Xác định các giá trị bị thiếu và các bản ghi trùng lặp.
* Hiểu được phân phối của các đặc trưng số và đặc trưng phân loại.
* Xác định mối quan hệ giữa các biến đầu vào và giá nhà.
* Phát hiện các đặc trưng có ảnh hưởng mạnh nhất đến biến mục tiêu.
* Xác định các giá trị ngoại lệ có thể ảnh hưởng đến hiệu suất của mô hình.
* Cung cấp những thông tin hữu ích cho giai đoạn Feature Engineering.
* Chuẩn bị một bộ dữ liệu sạch và đáng tin cậy trước khi huấn luyện mô hình Multilayer Perceptron (MLP) bằng PyTorch.

