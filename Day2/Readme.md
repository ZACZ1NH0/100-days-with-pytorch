### Day2: Gradient calculate with autograd

### autograd
autograd là cơ chế tự động tính đạo hàm trong PyTorch. Nó theo dõi các phép toán trên tensor có requires_grad=True, từ đó xây dựng đồ thị tính toán (computation graph) để gọi .backward() và tự động tính đạo hàm ngược.