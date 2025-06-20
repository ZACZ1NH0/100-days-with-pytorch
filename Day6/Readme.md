## Linear Regression

### Linear Regression là gì?

Là một thuật toán học có giám sát (supervised learning), dùng để dự đoán giá trị số dựa trên một (hoặc nhiều) đặc 

trưng đầu vào.

Là một mô hình thống kê đơn giản nhất trong học máy, Linear Regression dự đoán đầu ra y từ đầu vào x dựa trên một 

đường thẳng.

Công thức:

Với 1 biến đầu vào x:

 y^ = w * x + b

​
y^ : giá trị dự đoán

w: trọng số (weight)

b: độ lệch (bias)

### MSE Loss – Hàm mất mát

Sử dụng Mean Squared Error (MSE) để đo độ sai lệch:

Loss = 1/n * sum((y - y^)**2)

