### Activation function

Activation function (hàm kích hoạt) là hàm phi tuyến được áp 

dụng lên đầu ra của từng neuron, nhằm giúp mạng nơ-ron có khả 

năng học và biểu diễn các mối quan hệ phi tuyến giữa dữ liệu 

đầu vào và đầu ra.

_______________________________

Nếu không dùng hàm kích hoạt phi tuyến (chỉ dùng hàm tuyến tính 

như y = Wx + b), thì dù có bao nhiêu lớp đi nữa, toàn bộ mạng 

vẫn tương đương 1 lớp tuyến tính → không có "sức mạnh học sâu".

_______________________________

### Các loại hàm kích hoạt thường dùng

ReLU (Rectified Linear Unit)

        Công thức: f(x) = max(0, x)

        Đơn giản, hiệu quả, nhanh hội tụ.

Sigmoid

        Công thức: f(x) = 1 / (1 + exp(-x))

        Dùng trong binary classification (logistic regression).

        Dễ bị vanishing gradient (gradient nhỏ dần về 0 khi x quá lớn hoặc quá nhỏ).

Tanh (Hyperbolic Tangent)

        Công thức: f(x) = (exp(x) - exp(-x)) / (exp(x) + exp(-x))

        Range: (-1, 1)

        Tốt hơn sigmoid ở nhiều trường hợp vì trung tâm ở 0.

Leaky ReLU

        Khắc phục nhược điểm ReLU chết (ReLU = 0 với x < 0).

        Cho phép gradient nhỏ khi x < 0.

Softmax

        Dùng ở đầu ra của mạng phân loại nhiều lớp.

        Trả về xác suất cho mỗi class.






| Mục đích            | Hàm kích hoạt nên dùng         |
| ------------------- | ------------------------------ |
| Ẩn (hidden layer)   | ReLU, LeakyReLU, Tanh          |
| Phân loại nhị phân  | Sigmoid (cuối cùng)            |
| Phân loại nhiều lớp | Softmax (cuối cùng)            |
| Mạng hồi quy        | Không dùng activation ở output |
