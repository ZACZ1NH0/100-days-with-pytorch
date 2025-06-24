## Softmax & Cross Entropy

### Softmax

Softmax chuyển các đầu ra (logits) thành xác suất để mô hình có thể chọn lớp.

Softmax biến các điểm số (logits) thành xác suất, sao cho:

    Tổng xác suất = 1

    Lớp nào có điểm lớn → xác suất cao hơn.

Công thức:

    Softmax(zi) = e^(zi) / ∑(e^zj)

___
Ví dụ:

Bạn có một mô hình AI, nó phải chọn 1 trong nhiều lớp (ví dụ: hình là chó, mèo hay thỏ?).

Mô hình không nói thẳng "Tôi chắc chắn là mèo", mà nó sẽ nói bằng điểm số:
    Chó: 1.2
    Mèo: 3.3
    Thỏ: 0.5
Các con số này là logits (điểm chưa xử lý). Mình cần biến chúng thành xác suất.

### Cross Entropy Loss là gì?

Cross Entropy đo mức độ khác biệt giữa phân phối xác suất dự đoán và nhãn thật.

Với nhãn thật là one-hot vector y, và đầu ra dự đoán y^

    Loss = -∑ yi*log(yi^)* 1/N


Giả sử nhãn thật là “mèo” (class 1). Mà model lại bảo “tôi nghĩ 85% là mèo”, thì 

loss sẽ thấp.

Nhưng nếu model bảo “tôi nghĩ 5% là mèo”, thì loss cao.

Cross Entropy đo mức độ lệch giữa dự đoán và thực tế.