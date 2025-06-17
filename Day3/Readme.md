# Day 3:  Gradient Descent

## 1. Local minimum và Global minimum là gì?
Giả sử bạn đang đi bộ trên một con đường núi. Bạn có thể gặp nhiều chỗ trũng – điểm thấp nhất trong vùng đó – đó gọi là local minimum (cực tiểu địa phương).
Nhưng nếu bạn tìm được chỗ thấp nhất của toàn bộ con đường, đó gọi là global minimum (cực tiểu toàn cục).

          *
        *   *
     *         *       ← local minimum (cục bộ)
   *             *
 *                 *      ← global minimum (toàn cục)


## 2. Đạo hàm có ý nghĩa gì ở đây?

Trong toán, đạo hàm là độ dốc của hàm số tại một điểm. Nó cho bạn biết nếu bạn đi một bước nhỏ sang phải thì hàm số tăng hay giảm.
    Nếu đạo hàm âm ⇒ đồ thị đang đi xuống (trái sang phải).
    Nếu đạo hàm dương ⇒ đồ thị đang đi lên.
    Nếu đạo hàm = 0 ⇒ có thể là đỉnh hoặc đáy (cực trị).

Tại một local minimum, đạo hàm bằng 0, và:
    Trái của điểm đó đạo hàm âm (hàm đang giảm).
    Phải của điểm đó đạo hàm dương (hàm bắt đầu tăng).

## 3. Gradient Descent là gì?

Gradient Descent (GD) là một phương pháp tìm cực tiểu bằng cách đi theo hướng "dốc đi xuống nhất".
    Tưởng tượng bạn bị bịt mắt trên núi và muốn tìm điểm thấp nhất:
    Bạn sờ xung quanh, thấy bên trái dốc hơn ⇒ bạn đi về bên trái.
    Đi vài bước, lại kiểm tra độ dốc ⇒ đi tiếp về phía thấp hơn.
    Cứ lặp lại như thế, bạn sẽ dần dần đến điểm thấp nhất gần đó (local minimum).

🌟 Trong toán học, quá trình này là:

x_new = x_old - learning_rate * gradient

gradient là đạo hàm.
learning_rate là bước nhảy nhỏ bạn đi mỗi lần.
Cứ lặp lại đến khi gradient ≈ 0 ⇒ tìm được điểm cực tiểu.

## 4. Learning rate

Learning rate (tốc độ học) là siêu tham số quan trọng nhất trong huấn luyện mô hình học máy — nó điều khiển bước nhảy khi cập nhật trọng số w.

w = w - learning_rate * gradient

Nếu learning rate quá nhỏ:

    Mô hình học rất chậm (nhiều epoch mới hội tụ).

    Có thể không bao giờ đến được điểm tối ưu nếu dừng sớm.

Nếu learning rate quá lớn:

    Trọng số có thể nhảy quá xa, vượt qua điểm tối ưu.

    Có thể khiến mô hình dao động, không hội tụ hoặc diverge (sai số tăng mãi không giảm).

### Hình dung trực quan:

Giả sử bạn đang đi xuống một thung lũng để tìm điểm thấp nhất (minimum của hàm mất mát):

🔹 learning rate nhỏ: bạn đi từng bước nhỏ, rất chậm nhưng an toàn.

🔹 learning rate lớn: bạn nhảy từng bước dài, có thể nhảy qua lại giữa các sườn núi, không bao giờ đến đáy.

