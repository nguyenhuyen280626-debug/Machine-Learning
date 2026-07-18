# Dự đoán Giá Nhà

# Kỹ thuật Đặc trưng (Feature Engineering)

Feature Engineering là quá trình xử lý, biến đổi và lựa chọn các đặc trưng nhằm nâng cao chất lượng dữ liệu trước khi huấn luyện mô hình Machine Learning hoặc Deep Learning. Mục tiêu là giúp mô hình học hiệu quả hơn và cải thiện khả năng dự đoán.

Trong dự án này, dữ liệu sau khi được xử lý sẽ được sử dụng để huấn luyện mô hình Multilayer Perceptron (MLP) bằng thư viện PyTorch.

---

# 1. Kiểm tra chất lượng dữ liệu (Data Inspection)

Trước khi thực hiện Feature Engineering, bộ dữ liệu được kiểm tra để đảm bảo chất lượng.

Các bước thực hiện gồm:

- Kiểm tra kích thước của tập dữ liệu.
- Kiểm tra kiểu dữ liệu của từng thuộc tính.
- Kiểm tra các giá trị thiếu (Missing Values).
- Kiểm tra dữ liệu trùng lặp (Duplicate Records).

Kết quả cho thấy bộ dữ liệu không có giá trị thiếu và không có bản ghi trùng lặp nên không cần xử lý thêm.

---

# 2. Mã hóa biến phân loại (Label Encoding)

Bộ dữ liệu chứa một số thuộc tính dạng phân loại (Categorical Features).

Các biến này được chuyển thành dạng số bằng phương pháp Label Encoding để mô hình có thể xử lý.

Ví dụ:

- Ocean Proximity

Sau khi mã hóa, tất cả các thuộc tính đều ở dạng số.

---

# 3. Tạo đặc trưng mới (Feature Creation)

Để cung cấp thêm thông tin cho mô hình, một số đặc trưng mới được tạo từ các thuộc tính hiện có.

Bao gồm:

- Total_Rooms
- Room_Density

Các đặc trưng mới giúp phản ánh tốt hơn mối quan hệ giữa diện tích, số phòng và mật độ sử dụng của ngôi nhà.

---

# 4. Lựa chọn đặc trưng (Feature Selection)

Thực hiện phân tích hệ số tương quan (Correlation Analysis) giữa các đặc trưng và giá nhà.

Mục đích:

- Đánh giá mức độ ảnh hưởng của từng đặc trưng.
- Lựa chọn các đặc trưng quan trọng phục vụ huấn luyện mô hình.

---

# 5. Chuẩn hóa dữ liệu (Feature Scaling)

Sau khi lựa chọn đặc trưng, dữ liệu được chuẩn hóa bằng StandardScaler.

Quá trình chuẩn hóa giúp:

- Đưa các đặc trưng về cùng thang đo.
- Giúp mô hình MLP hội tụ nhanh hơn.
- Hạn chế ảnh hưởng của sự khác biệt về đơn vị đo giữa các thuộc tính.

---

# 6. Chia tập dữ liệu

Bộ dữ liệu được chia thành:

- Training Set (80%)
- Testing Set (20%)

Training Set được sử dụng để huấn luyện mô hình.

Testing Set được sử dụng để đánh giá khả năng dự đoán.

---

# 7. Chuyển dữ liệu sang Tensor

Sau khi tiền xử lý hoàn tất:

- Chuyển dữ liệu từ NumPy sang Tensor của PyTorch.
- Chuyển biến mục tiêu thành Tensor dạng vector cột.

Bước này giúp dữ liệu sẵn sàng để huấn luyện mô hình MLP.

---

# Kết quả đạt được

Sau khi hoàn thành Feature Engineering:

- Bộ dữ liệu sạch và nhất quán.
- Không có giá trị thiếu hoặc dữ liệu trùng lặp.
- Các biến phân loại đã được mã hóa.
- Các đặc trưng mới đã được tạo.
- Các đặc trưng đã được chuẩn hóa.
- Dữ liệu đã được chia thành Training Set và Testing Set.
- Dữ liệu đã được chuyển sang Tensor và sẵn sàng cho quá trình huấn luyện mô hình.