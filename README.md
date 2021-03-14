# Midterm
_ LHS và Minhash là 2 thuật toán có thể so sánh và tìm kiếm các tài liệu giống nhau trong tập hợp các tài liệu lớn.
_ Việc so sánh sẽ dựa vào độ giống nhau của mật độ từ (content similarity) không phải dựa trên độ giống nhau của ngữ nghĩa (semantic similarity).
_ Giả sử có một tập dữ liệu có n phần tử và hàm get_similarity(D1,D2). Hàm get_similarity(D1,D2) sẽ phải chạy n^2 lần và hàm phải so sánh từng từ trong tập D1 với từng từ trong tập D2 với m là số từ có trong mỗi tập. Hàm get_similarity(D1,D2) sẽ phải chạy (n^2) * m lần và 
 
