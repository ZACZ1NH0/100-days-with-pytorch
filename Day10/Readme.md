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

### Ví dụ 

Phân loại: Chó, Mèo, Gà

Ta có một mô hình phân loại 3 lớp:

    Lớp 0: Chó

    Lớp 1: Mèo

    Lớp 2: Gà

[2.0, 1.0, 0.1]  # mẫu 1

Sau khi đưa vào hàm softmax, ta nhận được:

torch.softmax(torch.tensor([2.0, 1.0, 0.1]), dim=0)

 ≈ [0.659, 0.242, 0.099]

👉 Mô hình “tin” rằng:

65.9% là Chó

24.2% là Mèo

9.9% là Gà

=> Dự đoán nhãn: Chó (vì xác suất cao nhất).


Nhãn thật (target) là số nguyên: 0, 1, hoặc 2

Với CrossEntropyLoss, không cần softmax thủ công.

Ta chỉ đưa logits thô vào, loss sẽ tự tính nội bộ:

        loss_fn = nn.CrossEntropyLoss()
        logits = torch.tensor([[2.0, 1.0, 0.1]])
        target = torch.tensor([0])
        loss = loss_fn(logits, target)
