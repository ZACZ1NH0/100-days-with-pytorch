## Logistic Regression

### Logistic Regression là gì?

Logistic Regression là 1 thuật toán phân loại được dùng để gán các đối tượng cho 1 tập hợp giá trị rời rạc (như 0, 1,

2, ...). Một ví dụ điển hình là phân loại Email, gồm có email công việc, email gia đình, email spam, ... Giao dịch 

trực tuyến có là an toàn hay không an toàn, khối u lành tính hay ác tình. Thuật toán trên dùng hàm sigmoid logistic để 

đưa ra đánh giá theo xác suất. Ví dụ: Khối u này 80% là lành tính, giao dịch này 90% là gian lận, ...

### Hàm sigmoid

Giá trị của hàm sigmoid sẽ nằm trong khoảng từ 0 đến 1, ta dùng giá trị này để phân loại xem gần với nhãn 0 hay 1 hơn 

(xác suất).

hàm sigmoid có dạng

1/(1+e^(-z))

trong đó z là hàm tuyến tính wx+b

### Hàm mất mát

Binary Cross-Entropy (Log Loss):

Loss = -y*log(y^) - (1-y)log(1-y^) 

Nếu nhãn thật là 1, ta muốn y^ gần 1

Nếu nhãn thật là 0, ta muốn y^ gần 0