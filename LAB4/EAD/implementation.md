# Dự đoán Giá Nhà

# Triển khai Mô hình (Model Implementation)

Sau khi hoàn thành bước Feature Engineering, dữ liệu được sử dụng để xây dựng và huấn luyện mô hình Multilayer Perceptron (MLP) bằng thư viện PyTorch nhằm dự đoán giá nhà.

---

# 1. Import thư viện

Các thư viện được sử dụng gồm:

## Xử lý dữ liệu

- NumPy
- Pandas

## Trực quan hóa

- Matplotlib
- Seaborn

## Deep Learning

- PyTorch
- torch.nn
- torch.optim

## Đánh giá mô hình

- Mean Squared Error (MSE)
- Mean Absolute Error (MAE)
- R-squared Score (R²)

---

# 2. Chuẩn bị dữ liệu

Sử dụng bộ dữ liệu đã được xử lý từ bước Feature Engineering.

Các bước:

- Tách dữ liệu thành X và y.
- Chia dữ liệu thành Training Set và Testing Set.
- Chuyển dữ liệu sang Tensor của PyTorch.

---

# 3. Xây dựng mô hình MLP

Mô hình được xây dựng bằng PyTorch với kiến trúc:

Input Layer

↓

Linear Layer (32 neurons)

↓

ReLU

↓

Linear Layer (16 neurons)

↓

ReLU

↓

Output Layer (1 neuron)

Output của mô hình là giá nhà dự đoán.

---

# 4. Hàm mất mát (Loss Function)

Sử dụng:

Mean Squared Error (MSELoss)

MSE đo sai số bình phương trung bình giữa giá trị dự đoán và giá trị thực.

Mục tiêu của quá trình huấn luyện là giảm giá trị Loss xuống mức thấp nhất.

---

# 5. Bộ tối ưu (Optimizer)

Sử dụng thuật toán Adam.

Adam giúp cập nhật trọng số nhanh, ổn định và hội tụ tốt đối với mạng nơ-ron.

---

# 6. Huấn luyện mô hình

Quá trình huấn luyện gồm các bước:

- Forward Propagation
- Tính Loss
- Backpropagation
- Cập nhật trọng số
- Lặp lại qua nhiều Epoch

Trong quá trình huấn luyện, giá trị Training Loss được lưu lại để theo dõi khả năng hội tụ của mô hình.

---

# 7. Đánh giá mô hình

Sau khi huấn luyện hoàn tất, mô hình được đánh giá trên tập Testing.

Các chỉ số sử dụng gồm:

## Mean Squared Error (MSE)

Đo sai số bình phương trung bình.

## Mean Absolute Error (MAE)

Đo sai số tuyệt đối trung bình.

## R-squared (R²)

Đánh giá mức độ giải thích của mô hình đối với dữ liệu.

---

# 8. Trực quan hóa kết quả

Biểu đồ Loss được vẽ theo từng Epoch.

Mục đích:

- Quan sát quá trình học của mô hình.
- Kiểm tra khả năng hội tụ trong quá trình huấn luyện.

---

# 9. Dự đoán giá nhà

Sau khi mô hình được huấn luyện, dữ liệu Testing được đưa vào mô hình để dự đoán giá nhà.

Kết quả dự đoán được sử dụng để tính các chỉ số đánh giá hiệu suất mô hình.

---

# Kết quả đạt được

Sau khi hoàn thành quá trình triển khai:

- Mô hình MLP được xây dựng thành công bằng PyTorch.
- Training Loss giảm dần theo Epoch.
- Mô hình dự đoán được giá nhà trên tập Testing.
- Hiệu suất mô hình được đánh giá bằng MSE, MAE và R².
- Hoàn thiện quy trình dự đoán giá nhà bằng Deep Learning.
