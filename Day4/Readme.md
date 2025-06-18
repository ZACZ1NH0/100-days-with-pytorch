# Optimizer

## Optimizer là gì?

Optimizer (thuật toán tối ưu) là công cụ giúp mô hình học ra các trọng số (weights và bias) tốt nhất bằng cách giảm dần hàm mất mát (loss function) sau mỗi lần lặp (epoch).

Thay vì thử ngẫu nhiên các trọng số, optimizer điều chỉnh chúng dựa trên đạo hàm (gradient).

Trong huấn luyện mô hình học sâu, optimizer là một thuật toán có nhiệm vụ tìm ra giá trị tối ưu cho trọng số (weights) và bias nhằm giảm thiểu hàm mất mát (loss function).

Nếu không có optimizer, chúng ta không thể cập nhật các trọng số sao cho mô hình học được từ dữ liệu. Optimizer sẽ dựa trên gradient (đạo hàm) của hàm mất mát để cập nhật trọng số theo một hướng giúp giảm loss.

Tóm lại: Optimizer là công cụ để “học” ra trọng số tốt nhất.

## Các thuật toán tối ưu phổ biến

### Gradient Descent (GD)

Ý tưởng:

Tìm cực tiểu của hàm mất mát bằng cách cập nhật các tham số theo hướng ngược lại của đạo hàm.


Công thức:
w_new = w_old - learning_rate * gradient

Nhược điểm: chậm, tốn tài nguyên với tập dữ liệu lớn.

### Stochastic Gradient Descent (SGD)

Stochastic là 1 biến thể của Gradient Descent . Thay vì sau mỗi epoch chúng ta sẽ cập nhật trọng số (Weight) 1 lần thì

trong mỗi epoch có N điểm dữ liệu chúng ta sẽ cập nhật trọng số N lần. Nhìn vào 1 mặt , SGD sẽ làm giảm đi tốc độ của
 
1 epoch. Tuy nhiên nhìn theo 1 hướng khác,SGD sẽ hội tụ rất nhanh chỉ sau vài epoch. Công thức SGD cũng tương tự như 
  
GD nhưng thực hiện trên từng điểm dữ liệu.


 
Cập nhật trọng số sau từng mẫu dữ liệu thay vì toàn bộ tập.

Nhanh, phù hợp với dữ liệu lớn và online learning.

Nhược điểm: cập nhật “giật cục”, dễ bị dao động.

### Momentum

Thêm "quán tính" vào SGD giúp tránh kẹt ở điểm cực tiểu cục bộ.

Công thức:

v = γ * v - lr * gradient  
w = w + v
(γ thường là 0.9)

Ý tưởng vật lý: giống như viên bi trượt xuống dốc, có đà nên vượt qua “ổ gà”.

### Adagrad

Tự điều chỉnh learning rate cho từng tham số, dựa trên gradient quá khứ.

Giúp học tốt hơn cho các tham số hiếm gặp.

g += ∇L(w)^2  
w = w - learning_rate / sqrt(g + ε) * ∇L(w)

Trong đó:

g: tổng bình phương gradient theo từng tham số

ε: số rất nhỏ tránh chia cho 0 (thường là 1e-8)

🔸 Ưu điểm:
Không cần tuning learning rate

Phù hợp với dữ liệu rời rạc (như xử lý từ ngữ - NLP)

🔸 Nhược điểm:
Tổng gradient tăng liên tục → learning rate giảm dần về gần 0 → mô hình không học được nữa

### RMSprop

Giải quyết nhược điểm của Adagrad bằng cách dùng trung bình động của bình phương gradient, thay vì cộng dồn mãi.

Công thức:

    E[g^2] = ρ * E[g^2] + (1 - ρ) * ∇L(w)^2  

    w = w - learning_rate / sqrt(E[g^2] + ε) * ∇L(w)

Trong đó:

ρ: hệ số trượt trung bình động (thường là 0.9)

E[g^2]: giá trị trung bình động của gradient bình phương

🔸 Ưu điểm:

Giữ tốc độ học ổn định

Tốt với dữ liệu có gradient thay đổi nhanh

🔸 Nhược điểm:

Có thể vẫn kẹt ở local minimum nếu gradient không đủ mạnh để vượt qua

### Adam

Kết hợp Momentum và RMSprop để tận dụng ưu điểm cả hai: vừa mượt mà vừa thích ứng được tốc độ học.

Tổng hợp ưu điểm của Momentum và RMSprop.

Tự động điều chỉnh tốc độ học và hướng di chuyển.

Được dùng phổ biến nhất hiện nay vì hiệu quả và ổn định.

🔸 Công thức:

Adam dùng 2 giá trị trung bình:

Momentum (m): trung bình động của gradient

RMS (v): trung bình động của bình phương gradient

m_t = β1 * m_{t-1} + (1 - β1) * g_t  
v_t = β2 * v_{t-1} + (1 - β2) * g_t^2

m_hat = m_t / (1 - β1^t)  
v_hat = v_t / (1 - β2^t)  

w = w - learning_rate * m_hat / (sqrt(v_hat) + ε)

🔸 Ưu điểm:

Phổ biến nhất trong thực tế

Tự động điều chỉnh learning rate và giảm dao động

Hội tụ nhanh, ổn định

🔸 Nhược điểm:

Cần nhiều bộ nhớ hơn để lưu trạng thái (momentum + squared gradient)

Nếu quá phụ thuộc có thể dẫn đến overfitting nhẹ

| Optimizer | Cập nhật trên | Learning Rate | Ghi nhớ quá khứ? | Tự điều chỉnh LR? | Dễ dùng? |
| --------- | ------------- | ------------- | ---------------- | ----------------- | -------- |
| GD        | Toàn bộ tập   | Cố định       | ❌                | ❌                 | ✅        |
| SGD       | Từng mẫu      | Cố định       | ❌                | ❌                 | ✅        |
| Momentum  | Từng mẫu      | Cố định       | ✅                | ❌                 | ✅        |
| Adagrad   | Từng mẫu      | Biến thiên    | ✅ (g^2 cộng dồn) | ✅                 | ✅        |
| RMSprop   | Từng mẫu      | Biến thiên    | ✅ (trung bình)   | ✅                 | ✅        |
| Adam      | Từng mẫu      | Biến thiên    | ✅ (m + v)        | ✅                 | ✅✅✅   |
