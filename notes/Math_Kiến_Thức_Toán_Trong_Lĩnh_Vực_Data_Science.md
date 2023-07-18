---
title: 'Kiến Thức Toán Trong Lĩnh Vực Data Science'
date: '2020-01-02'
type: math
---

# Kiến Thức Toán Trong Lĩnh Vực Data Science
Để bắt đầu học Machine Learning hay Data Science, người học sẽ bị choáng ngợp bởi khối lượng kiến thức đồ sộ liên quan đến lĩnh vực Toán học. Đây cũng là điều hiển nhiên bởi Toán học luôn là nền tảng cho bất kỳ ngành Khoa học đương đại nào. 
Sự vững chắc về nền tảng toán học hình thành đằng sau các thuật toán sẽ tạo cho bạn một lợi thế không hề nhỏ so khi nghiên cứu và làm việc ở lĩnh vực Data Science. Bởi hơn hết, doanh nghiệp luôn chỉ trả rất nhiều tiền cho công nghệ bên trong máy móc thay vì người vận hành vốn không có bất kỳ kiến thức chuyên sâu nào về chúng. 
Bảo gửi đến các bạn ví dụ để tìm hiểu chuyên sâu hơn cho quy trình khoa học phổ biến trong xử lý âm thanh:
- Khai thác thông tin, tính chất vật lý của âm thanh và mô hình hóa quá trình hình thành.
- Xây dựng giả thuyết hình thành về âm thanh.
- Ước tính độ chất lượng của nguồn dữ liệu thu thập được.
- Định lượng sự không chắc chắn xung quanh dữ liệu và dự đoán.
- Xác định mẫu ẩn từ luồng thông tin.
- Khai thác và tìm hiểu giới hạn của một mô hình.
- Nghiên cứu bằng chứng toán học và logic trừu tượng.

Qua đó, ta có thể thấy bản chất của Data Science không gắn liền với một lĩnh vực hay một chủ đề cụ thể mà còn có thể xử lý rất nhiều vấn đề, hiện tượng đa dạng như chuẩn đoán bệnh ung thư hay dự báo thời tiết.

## 1) Tìm hiểu về biến, hàm số, phương trình và đồ thị
Kiến thức về Toán mà chúng ta học từ thời trung học các bạn hãy  cùng Bảo tổng hợp một số nền tảng cơ bản này:
- Hàm số logarit, hàm mũ, hàm số đa thức, số hữu tỉ.
- Hình học và định lý cơ bản, kiến thức về lượng giác.
- Số thực và số phức cùng những tính chất cơ bản.
- Kiến thức về chuỗi, tổng, bất đẳng thức.
- Vẽ và biểu diễn đồ thị, kiến thức về tọa độ Descartes và toạ độ cực, đường conic.
### Những kiến thức này vận dụng ra sao ?
Ví dụ về thuật toán tìm kiếm như việc bạn tìm kiếm số thứ tự của mình trong phòng thi trong danh sách.

Các bạn có thể nắm khái quát: Thuật toán sắp xếp đơn thuần là việc sắp xếp các phần tử trong danh sách theo thứ tự tăng và giảm dần. Với lập trình cài đặt trên máy tính thì từng thuật toán sắp xếp khác nhau sẽ thực hiện trong các mốc thời gian khác nhau. Thuật toán thực hiện nhanh hay chậm còn phụ thuộc vào các yếu tố khác như kích thước bộ dữ liệu, độ phức tạp của thuật toán, etc.

Nếu chúng ta ứng dụng thuật toán  “Binary Search” để tối ưu việc tìm kiếm trên cơ sở dữ liệu với hàng chục triệu phần tử thì sẽ không gặp vấn đề khó khăn. Để tối ưu hóa được chương trình  chúng ta áp dụng khái niệm logarit 

Để một chương trình tìm kiếm được tối ưu, ta phải cần hiểu về khái niệm logarit lẫn sự lặp lại của phương trình. Qua việc tính toán trong thời gian chạy logarit, bạn có thể hình dung ra những không gian tìm kiếm phù hợp cho thuật toán nhằm xây dựng cấu trúc dữ liệu phù hợp.

Chính vì thế "Binary Search" luôn xuất hiện nhiều biến thể với hiệu suất ngày càng tăng.
Tham khảo Binary search Algorithm: https://en.wikipedia.org/wiki/Binary_search_algorithm
 
### Bạn có thể bổ sung kiến thức về Toán ở đâu ?
- Website Machine Learning cơ bản: https://machinelearningcoban.com/math/[[luu-y-ve-ky-hieu]]
- Data Science Math Skills - Coursera: https://www.coursera.org/learn/datasciencemathskills
- Introduction to Algebra - edX: https://www.edx.org/course/introduction-algebra-schoolyourself-algebrax-1
- Algebra I - Khan Academy: https://www.khanacademy.org/math/algebra

## 2) Kiến thức về Thống kê (Statistics)
 
Cho tới nay, nhiều bạn thường cho rằng Thống kê chủ yếu thuộc về phạm trù Kinh tế. Nhưng có lẽ bạn sẽ bất ngờ thực sự vì chúng liên quan đến Data Science rất nhiều là đằng khác.

Có thể nói nếu bạn đã theo lĩnh vực Data Science việc hiểu biết Lập trìn hay ngôn ngữ cũng chỉ là công cụ. Cái cốt lõi mà người học Data Science lẫn Machine Learning (Máy học) **phải nắm thật vững là Toán và Xác suất thống kê.**

Nếu nói theo một cách tán gẫu, ta còn có một công thức: **Data Science = Big Data + Statistics + Computer Science**

Và hiện nay thì Việt Nam chúng ta luôn đầy rẫy những vấn đề thực tế. Với chủ đề rộng lớn như vậy thì việc lập ra kế hoạch là vô cùng quan trọng để đảm bảo chúng ta luôn bao quát mọi thứ:
- Tóm tắt dữ liệu và thống kê mô tả, xu hướng trung tâm, phương sai, hiệp phương sai, tương quan
- Xác suất cơ bản: cơ bản, kỳ vọng, tính toán xác suất, định lý Bayes, xác suất có điều kiện
- Các hàm phân phối xác suất: thống nhất, bình thường, nhị thức, bình phương, định lý giới hạn trung tâm
- Lấy mẫu, đo lường, tạo số ngẫu nhiên
- Kiểm tra giả thuyết lẫn độ tin cậy, độ lỗi,...
- Hồi quy tuyến tính, kỹ thuật chính quy hoá
 
### Những kiến thức này vận dụng ra sao ?
Những kiến thức về Toán, Thống kê,... chính là điểm khác biệt trong Mindset của một Data Science. Nhiệm vụ của bạn chính là đặt câu hỏi và tìm hiểu thật kỹ vấn đề thực tế mình cần giải quyết. Một khi vấn đề được xác định thì đó là lúc bạn sẽ tiến hành thu thập dữ liệu và phân tích thật kỹ lưỡng không khác gì Sherlock Holmes.

Với kiến thức về Toán lẫn Thống kê, bạn có thể tự đặt ra những giả thuyết về dữ liệu mình đang xét hay phán đoán kết quả từ giải thuyết và không ngừng hình thành những câu hỏi mới nhằm phân tích dữ liệu thật chuẩn xác.

### Bạn có thể bổ sung kiến thức về Thống kê ở đâu ?
- Statistics and Probability in Data Science using Python - edX: https://courses.edx.org/courses/course-v1:UCSanDiegoX+DSE210x+3T2017/course/
- Data Science - D2Academics: https://d2academics.thinkific.com/courses/take/data-science/
- Statistics with R Specialization - Coursera: https://www.coursera.org/specializations/statistics
- Business Statistics and Analysis Specialization - Coursera: https://www.coursera.org/specializations/business-statistics-analysis
- (Sách tiếng Việt) Phân Tích Dữ Liệu Với R – Hỏi Và Đáp (Tái Bản 2018) - Nguyễn Văn Tuấn

 ## 3) Đại số tuyến tính
 
Bạn có bao giờ thắc mắc khi lướt Facebook và nhận được gợi ý kết bạn hay việc Netflix luôn gợi ý các phim phù hợp với sở thích bản thân mình. Đó được gọi là Recommend System với các thuật toán được triển khai trong quá trình thu thập, phân tích dữ liệu về thông tin, xu hướng người dùng để đưa ra các gợi ý phù hợp cho người dùng trên hệ thống.

Tại đây, kiến thức Đại số tuyến tính sẽ được áp dụng giúp chúng ta hiểu chuyên sâu hơn cách thuật toán học máy hoạt động trên luồng dữ liệu. Từ đó các Data Scientist sẽ dễ dàng phân tích, xử lý insight trong dữ liệu một cách chi tiết nhất.

Hãy cùng AI VIET NAM tìm hiểu những kiến thức cơ bản về Đại số tuyến tính cần có nào:
- Các tính chất cơ bản của ma trận và vector: phép nhân vô hướng, biến đổi tuyến tính, chuyển vị, liên hợp, ...
- Quy tắc nhân ma trận và các thuật toán khác nhau, nghịch đảo ma trận
- Các Ma trận đặc biệt: ma trận vuông, ý tưởng về ma trận thưa thớt và dày đặc, vector đơn vị, ma trận đối xứng, ma trận đơn vị,...
- Mô hình phân tích ma trận thành nhân tử (Matrix Factorization) / phân tích LU, loại bỏ Gaussian / Gauss-Jordan, giải hệ phương trình tuyến tính Ax = b
- Cơ sở không gian vector, tính trực giao, bình phương tuyến tính nhỏ nhất
- Vector riêng & giá trị riêng trong ma trận, chéo hoá ma trận, phương pháp Singular Value Decomposition (SVD)
 
### Kiến thức này được ứng dụng ra sao?
Tất cả các thuật toán neural network đều sử dụng các kỹ thuật đại số tuyến tính để biểu diễn và xử lý các cấu trúc mạng lẫn huấn luyện dữ liệu. Kiến thức Đại số tuyến tính còn ứng dụng trong xử lý ảnh hay các thao tác, biểu diễn dữ liệu thực tế.
### Tôi có thể học chúng từ đâu?
- Linear algebra: foundations to frontiers - edX: https://courses.edx.org/courses/course-v1:UTAustinX+UT.5.05x+2T2017/course/
- Mathematics for Machine Learning: Linear Algebra - Coursera: https://www.coursera.org/learn/linear-algebra-machine-learning
- Python cho Đại số Tuyến tính - Machine learning Cơ bản: https://fundaml.com/course/5990a766cdc6e32b3b4d0666/intro
- Kiến thức về Đại số Tuyến tính cũng được đề cập kết hợp quiz + assignment để kiếm tra kiến thức tại Week một khoá Machine Learning - Coursera: https://www.coursera.org/learn/machine-learning
 
## 4) Giải tích (Calculus)
 
Giải tích chắc hẳn là một trong những môn học đại cương khá "ám ảnh" đối với sinh viên khối Khoa học - Kỹ thuật lẫn Kinh tế. Nhưng bất luận thực trạng sinh viên sợ hãi môn học ra sao thì Giải tích vẫn xuất hiện tất yếu trong Machine Learning lẫn Data Science.

Giải tích hình thành nên các giải pháp phân tích tưởng chừng cơ bản như Hồi quy tuyến tính (Linear Regression). Mà hơn hết, khi xây dựng một mô hình thuật toán máy học để phân tích và dự đoán giả thuyết dữ liệu thì Giải tích sẽ đóng vai trò quan trọng trong quy trình tìm độ lỗi cực tiểu cho mô hình và tối ưu hoá độ chính xác của mô hình.

Đây là một môn học khó nhưng sẽ cực kỳ giá trị nếu bạn được trang bị kiến thức Giải tích trên con đường trở thành Data Scientist. Hãy cùng Ad tìm hiểu những kiến thức cơ bản cần nắm nào:

- Kiến thức về Hàm số một biến, giới hạn, liên tục, khác biệt
- Các định lý về giá trị trung bình (Mean value theorems), các dạng không xác định, quy tắc L'Hospital
- Tính cực đại và cực tiểu của hàm số
- Quy tắc nhân (Product rule), Quy tắc dây chuyền (Chain rule)
- Chuỗi Taylor, khái niệm tổng hợp / tích hợp chuỗi vô hạn
- Các định lý giá trị cơ bản và trung bình của phép tính tích phân, đánh giá tích phân xác định và không xác định
- Hàm Gamma và hàm Beta
- Kiến thức về Hàm số nhiều biến, giới hạn, liên tục, đạo hàm riêng
- Khái niệm cơ bản của phương trình vi phân

### Tôi sẽ sử dụng kiến thức này ở đâu?
Bạn đã bao giờ từ hỏi thuật toán Logistic Regression thực hiện như thế nào? Phải chăng là chúng sử dụng phương pháp mang tên "Gradient Descent" để tìm hiểu hàm mất mát tối thiểu. Để hiểu cách thức hoạt động của nó, bạn cần nắm các khái niệm về độ dốc, đạo hàm, giới hạn hàm số lẫn quy tắc chuỗi.
- Tham khảo thuật toán Logistic Regression: https://machinelearningcoban.com/2017/01/27/logisticregression/

### Tôi có thể bổ sung kiến thức Giải tích ở đâu ?
- Pre-university calculus - edX: https://www.edx.org/course/pre-university-calculus
- Calculus I - Khan Academy: https://www.khanacademy.org/math/calculus-1
- Mathematics for machine learning: Multivariable calculus - Coursera: https://www.coursera.org/learn/multivariate-calculus-machine-learning
 
## 5) Toán rời rạc (Discrete Math)
 
Data Science hiện nay được thực hiện với sự trợ giúp của các hệ thống tính toán và Toán rời rạc là trung tâm của các hệ thống ấy.
Toán rời rạc sẽ bao gồm các khái niệm quan trọng đối với việc sử dụng hàng ngày các thuật toán và cấu trúc dữ liệu trong những project phân tích:
- Tìm hiểu về phép đếm, tổ hợp,...
- Nắm những kỹ thuật chứng minh cơ bản
- Khái niệm cơ bản của logic quy nạp, suy diễn và mệnh đề
- Hiểu được Cấu trúc dữ liệu cơ bản: ngăn xếp, hàng đợi, đồ thị, mảng, bảng băm, cây
- Những niệm cơ bản của Đồ thị và ứng dụng
- Hệ thức truy hồi

### Tôi có thể bổ sung kiến thức này ở đâu ?
Ví dụ khi phân tích về bài toán hành vi người dùng mạng xã hội, dữ liệu có thể được mô phỏng như các thuộc tính của biểu đồ và ta cần nghiên cứu thuật toán nhanh nhất để tìm kiếm lẫn duyệt qua từng điểm đồ thị. Và việc học cấu trúc rời rạc sẽ giúp bạn tìm hiểu độ phức tạp của thuật toán ở những không gian và thời gian khác nhau. Từ đó sẽ giúp bạn chọn lựa thuật toán phù hợp để giải quyết vấn đề của mình.

### Tôi có thể học Toán rời rạc ở đâu?
- Introduction to Discrete Mathematics for Computer Science Specialization - Coursera: https://www.coursera.org/specializations/discrete-mathematics
- Master discrete mathematics: sets, math logic, and more - Coursera: https://www.udemy.com/master-discrete-mathematics/
- Introduction to Mathematical Thinking - Coursera: https://www.coursera.org/learn/mathematical-thinking

---
Tags: [[Templates/Formatting/LaTeX/math]] -  [[Data Science]]
Reference:
Related: 