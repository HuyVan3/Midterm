# Midterm
- LHS và Minhash là 2 thuật toán có thể so sánh và tìm kiếm các tài liệu giống nhau trong tập hợp các tài liệu lớn.
- Việc so sánh sẽ dựa vào độ giống nhau của mật độ từ (content similarity) không phải dựa trên độ giống nhau của ngữ nghĩa (semantic similarity).
- Giả sử có một tập dữ liệu có n phần tử và hàm get_similarity(D1,D2). Hàm get_similarity(D1,D2) sẽ phải chạy n^2 lần và hàm phải so sánh từng từ trong tập D1 với từng từ trong tập D2 với m là số từ có trong mỗi tập. Hàm get_similarity(D1,D2) sẽ phải chạy (n^2) * m lần và không thực tế nếu thực thi trên bộ dữ liệu lớn.
# Shingling
- Cách hiệu quả nhất để thể hiện một tập tài liệu là sử dụng một tập hợp các chuỗi ngắn xuất hiện trong tài liệu đó. Nếu làm như vậy các tài liệu có các câu giống nhau trong nội dung sẽ có điểm chung trong tập hợp của chúng.
- Với k-shingles là một chuỗi con có độ dài k được tìm thấy trong tài liệu. Sau đó ta có thể kết hợp với một tài liệu khác với k-Shingles  xuất hiện một hoặc nhiều lần trong tập tài liệu đó.
- Độ lớn k phụ thuộc vào số tập tài liệu và tập hợp các kí tự. Chúng ta nên nhớ rằng k không nên được chọn quá thấp vì như thế tập k ký tự sẽ xuất hiện rất nhiều trong các tài liệu dù tài liệu đó không có cùng câu văn và trích dẫn.
# Preliminary-hashing (Optional)
- Bước này không bắt buộc vì chỉ làm được nếu có thể map được k-shingles với một số nguyên. 
- Nếu map được các k-shingles thì chúng ta biểu thị các tài liệu dưới dạng các hashed-shingle tuy nhiên số lượng các hashed-shingle không đồng đều giữa các tài liệu với nhau nếu tài liệu D1 lớn hơn D2 thì số lượng hashed-shingles của D1 sẽ nhiều hơn D2.
# Kiểm tra độ giống giau với Jaccard Score
- Jaccard score sẽ trả về giá trị trong khoảng [0,1] dựa trên mức độ giống nhau của các tập dữ liệu. Giá trị này được tính bằng hiệu số giữa phần giao của 2 tập hợp với phần hợp của 2 tập.
![jaccard](https://miro.medium.com/max/700/1*XiLRKr_Bo-VdgqVI-SvSQg.png)
# MinHash
- Tập hợp các k-shingles rất lớn dù có hash hay không vì thế mục đích của chúng ta là thay thế các k-shingles bằng các signatures nhỏ hơn. Các signature phải thể hiện ước lượng gần đúng về độ giống nhau của các tập tài liệu mà nó đại diện, signature càng lớn thì ước lượng càng chính xác.
- Các signature này vẫn giữ được nội dung của tài liệu mà nó đại diện. Nếu lấy 2 signature của 2 tài liệu giống nhau đem đi so sánh thì sẽ thấy được nhiều điểm tương đồng và ngược lại
- Thuật toán MinHash sẽ tạo ra các signature phù hợp với yêu cầu trên. 

# Locality-sensitive hashing (LSH)
- Thuật toán Locality-sensitive hashing là một kỹ thuật tính toán băm các item đầu vào giống nhau vào các "bộ chứa" (chunk, bucket) với xác suất cao. Vì các item giống nhau kết thúc trong cùng một bộ chứa, kỹ thuật này có thể được sử dụng để phân cụm dữ liệu và tìm kiếm lân cận. Nó khác với các kỹ thuật băm thông thường ở việc các va chạm băm được tối đa hóa, không được giảm thiểu.
- Sử dụng thuật toán này chúng ta sẽ băm đầu vào là các signature vào các "bộ chứa" (chunk, bucket). Bây giờ chúng ta có thể lấy ngẫu nhiên một chunk của một signature và so sánh với một chunk khác của một signature khác
![bucket](https://mrhasankthse.github.io/riz/assets/images/Bucket-distribution.png)
