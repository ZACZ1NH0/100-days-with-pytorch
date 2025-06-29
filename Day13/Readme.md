### CNN (Covolution neural network)

#### 🎯 1. CNN là gì?

CNN (Convolutional Neural Network) là mạng nơ-ron chuyên xử lý dữ liệu có dạng lưới, đặc biệt là hình ảnh (image).

Thay vì dùng nn.Linear như Feedforward, CNN sử dụng Convolutional layers (tầng tích chập) để trích xuất đặc trưng (feature extraction) từ ảnh.

#### 📷 2. Tại sao cần CNN thay vì dùng MLP cho ảnh?

Ví dụ một ảnh 28x28 pixels → 784 đầu vào. Nếu dùng MLP:

    Lượng tham số rất lớn

    Không khai thác được cấu trúc không gian (local structure) của ảnh

CNN giải quyết điều này bằng:

    Kernel nhỏ (3x3, 5x5) → quét qua từng vùng ảnh

    Tái sử dụng trọng số

    Giữ nguyên liên kết cục bộ (local connectivity)

#### 🧱 3. Cấu trúc mạng CNN cơ bản

    Input image (WxH)
    ↓
    Conv layer → ReLU → MaxPooling
    ↓
    Conv layer → ReLU → MaxPooling
    ↓
    Flatten
    ↓
    Fully Connected Layer(s)
    ↓
    Output (Softmax/Sigmoid)

#### 🧠 4. Các thành phần chính

| Thành phần        | Vai trò                         |
| ----------------- | ------------------------------- |
| `Conv2d`          | Tầng tích chập: trích đặc trưng |
| `ReLU`            | Phi tuyến                       |
| `MaxPool2d`       | Giảm chiều, giữ đặc trưng mạnh  |
| `Flatten`         | Biến từ tensor 2D → 1D          |
| `Linear`          | Dự đoán đầu ra                  |
| `Softmax/Sigmoid` | Phân loại đầu ra                |





