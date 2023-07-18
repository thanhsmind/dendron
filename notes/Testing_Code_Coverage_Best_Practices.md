---
title: 'Code Coverage Best Practices'
date: '2020-01-02'
type: programing 
---

# Testing Code Coverage Best Practices


***Code Coverage*** Có thật sự có giá trị hay không?

 ***Code Coverage*** cung cấp nhiều lợi ích cho quá trình develop. Chỉ số ***Code Coverage*** không thể hiện hoàn toàn chất lượng của việc Test nhưng nó là 1 chỉ số giúp team có thể action được. Nó cung cấp 1 thước đo hợp lý, khách quan, phù hợp với tiêu chuẩn ngành. Nên kết hợp chỉ số này với các phương thức Test khác sẽ giúp có cái nhìn tổng thể về chất lượng của hệ thống.

***Code Coverage*** có làm giảm lỗi trong hệ thống?
Việc giảm lỗi trong hệ thống hay không còn tùy vào nhiều yếu tố như viết có đúng không? Phủ đúng chỗ hay không? Nhưng nếu 1 team thật sự nghiêm túc trong việc phủ ***Code Coverage*** trong lâu dài sẽ giúp trình độ team lên cao, cẩn thận hơn, hiểu rõ về những gì mình viết, từ đó giảm lỗi rất nhiều. Khi thành thạo thành flow, sẽ không quá khó hay mất thời gian để có thể hoàn thành việc phủ ***Code Coverage***. 

Chỉ số ***100% Code Coverage*** cao có đảm bảo chất lượng test coverage?
Không. 100% Code coverage không hẳn là quá tốt. Nó là Team nhận định sai về độ an toàn của ứng dụng. Rất dễ nhầm tưởng nó hoàn hảo. 100% khiến ứng dụng chứa rất nhiều những code test nhỏ nhặt kém chất lượng, dẫn tới phí duy trì rất cao và gây nản khi phát triển sản phẩm.  Code Coverage không đảm bảo từng dòng code, từng nhánh ***hoạt động hoàn toán chính xác***, nó chỉ bảo đảm rằng đoạn code đó đã được phủ bởi ***test***. Tránh những copy/pasting tests hay những test được viết ráng cho đạt đủ số lượng. 

***Code Coverage*** có chỉ số quá thấp có tốt không?
Chỉ số ***Code Coverage*** không phải dùng đề highlight số lượng code đã phủ được test, mà nó cho thấy ở khía cạnh ngược lại. Số code bạn chưa cover test. Với chỉ số ***Code Coverage*** quá thấp cho thấy rằng còn rất nhiều phần trong sản phẩm chưa được test. Điều này tiềm ẩn nhiều lỗ hổng, và cho thấy bạn đang nhiều khả năng đưa những code xấu lên trên production. 

Vậy bao nhiêu % ***Code Coverage*** là tốt nhất?
Không có 1 số cố định nào để nói bao nhiêu % ***Code Coverage*** là tốt cả. Quan trọng là phải xác định những phần nào mình cần phải phủ test:
 - Những tính năng business quan trọng và có độ ảnh hưởng cao phải được test
 - Những đoạn code, branch thường xuyên thay đổi nên được test
 - Những phần phức tạp trong hệ thống.
Không có được 1 số x% nào cụ thể chung cho toàn bộ sản phẩm và công ty. Nó phụ thuộc vào quyết định đầu tư của công ty đối với sản phẩm. Chỉ số X càng cao, càng cần đầu tư ( nhân lực, infrastructure...), hay phải chỉnh chu lại quy trình để tích hợp vào quy trình develop, giúp tự động hóa việc chạy test từ đó quy trình sẽ nhanh hơn, nhưng sẽ cần đầu tư hơn.
Tại google có một vài X code coverage giúp tham chiếu khi chọn lựa: 
 - 60% accptable
 - 75% commendable
 - 90% exemplary.
 ___Lưu ý___: Không nên quá tập trung để nâng số 90% => 95% code coverage. Khi đạt mức này thì tăng lên nữa không quá ảnh hưởng. Nhưng nếu số x% code coverage quá thấp thì nên tập trung tăng lên 70%. và bảo đảm những phần code mới nên được cover bởi test để duy trì. 
 
 Đọc chỉ số ***Code Coverage*** thế nào cho hiệu quả? 
 Với chỉ số ***Code Coverage***, sẽ hiệu quả hơn khi nhìn ngược lại. Bao nhiêu x% chưa được cover bởi test, những phần đó có quan trọng không? Có những rủi ro gì nếu mình không test nó? Việc thêm code coverage giúp quá trình review code nhanh và hiệu quả hơn. 
 
Tôi đang có 1 cục code hệ thống cũ khá lớn và chẳng có code coverage gì cả, Tôi có nên làm?
Việc có 1 sản phẩm với low code coverage không có nghĩa là bạn không thể làm nó tốt lên. Dù rằng nó không dễ dàng. Thử áp dụng nguyên tắc "[[Cleancode Boy Scout Rule]]". Dần dần mọi thứ sẽ tốt lên. 

Nên nhớ Unittest chỉ là 1 phần của bức tranh. Integration/System Test cũng rất quan trọng. Nên có 1 bảng tổng hợp tất cả các loại Test sẽ giúp Team có cái hình tổng thể về tất cả. 

Team nên có 1 chỉ số thể hiện sự an toàn của code khi đưa lên production. Nó giúp Team có thể kiểm soát được chất lượng của code. Những phần nào vi phạm tiêu chuẩn nên bị reject không đưa vào production.





[Source](https://testing.googleblog.com/2020/08/code-coverage-best-practices.html)


---
Tags: [[Testing]] - [[Unittest]] -  [[CodeCoverage]]