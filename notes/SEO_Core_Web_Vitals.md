# SEO Core Web Vitals

## Core Web Vitals là gì?
Core Web Vitals là bộ các yếu tố Google đưa ra để đánh giá trải nghiệm người dùng trên 1 trang web. Bộ chỉ số này đo lường 3 khía cạnh:
- Tốc độ hiển thị nội dung
- Các tương tác với trang web có bị chậm trễ hay không?
- Nội dung hiển thị có hiển thị ổn định, mượt mà không?
## Core Web Vitals ảnh hưởng thế nào SEO?
Core Web Vitals là 1 chỉ số quan trọng trong các yếu tố ảnh hưởng tới thứ hạng của website trên Google. Google ưu tiên các website có trải nghiệm tốt với người dùng, ưu tiên mobile. 
## Chỉ số quan trọng Core Web Vitals
Google sử dụng 3 chỉ số để đo lường trải nghiệm của người dùng trên trang web:
- **LCP**: Thời gian hiển thị nội dung lớn nhất 
- **FID**: Thời gian phản hồi tương tác đầu tiên
- **CLS**: Điểm số tổng hợp về sự thay đổi bố cục
![[Core-Web-Vital-tong-quan.png]]
### LCP - Thời gian hiển thị nội dung lớn nhất
#### LCP là gì?
"LCP - Largest content paint chỉ số đo thời gian để trình duyệt hiển thị phần tử nội dung lớn nhất trong khung nhìn, tính từ khi người dùng yêu cầu URL"
Phần tử lớn nhất thường là hình ảnh hoặc Video hoặc phần tử text có khối lớn.

![[LCP-la-gi-Core-web-vital.png]]

Như ví dụ trên, Ảnh Cover của bài báo được coi là phần từ lớn nhất, thời gian được tính thời điểm yêu cầu URL tới khi hình ảnh load xong chính là thời gian đo của chỉ số LCP

==Nhiều khi phần tử lớn nhất của trang web lại không phải là phần tử quan trọng nhất của==
![[Instagram-LCP-Core-Web-Vital.png]]
Ví dụ trên, phần tử quan trọng nhất là logo Instagram, nhưng phần tử quan trọng nhất là nút Login

#### Chỉ số này có ý nghĩa thế nào với người dùng?
Thông thường phần lớn nhất hiển thị trên site là phần thông tin quan trọng nhất. Nếu phần quan trọng nhất này được load nhanh => người dùng nhanh đọc được thông tin học tìm kiếm => Bounce Rate sẽ giảm, Time on-page tăng => Trải nghiệm tốt => Google đánh giá chất lượng cao => Hiển thị cao trong kết quả Search.

#### Chỉ số LCP thế nào thì coi là nhanh?
**LCP** < 2.5s  sẽ được coi là nhanh. Được đo bằng công cụ Google Page Speed
![[Danh-gia-LCP-Core-Web-Vital.png]]

#### [Làm sao tối ưu chỉ số LCP](https://web.dev/optimize-lcp/)]
##### Tối ưu các đoạn JavaScript, code CSS không quan trọng
##### Cải thiện chất lượng Server
   Tối ưu server Backend làm sao cho trả lại kết quả với thời gian nhanh nhất. Một số gợi ý:
   - Phân tích và cải thiện sự hiệu quả, tinh gọn lại phần code Backend
   - Sử dụng các dịch vụ CDN
   - Sử dụng cache cho Backend
   #####  Tối ưu hình ảnh
   Hình ảnh càng nhẹ, load càng nhanh, sẽ giảm thời gian load của trang. Thông thường hình ảnh sẽ thường được dùng làm banner cover là phần lớn nhất của trang. 
   Hình ảnh trước khi được đẩy nên, nên được tối ưu về dung lượng và định dạng. Ưu tiên sử dụng các format:
   - JPEG 2000
   - JPEX XR
   - Web P
     [Tinypng.com] công cụ phổ biến và hiệu quả cho giảm kích thước hình ảnh. 
     Loại bỏ hình ảnh không cần thiết, hoặc sử dụng CDN cho hình ảnh.
     [Hướng dẫn SEO hình ảnh lên TOP Google: 7 bước đơn giản (seongon.com)](https://seongon.com/blog/seo/seo-hinh-anh.html)
##### Nén các định dạng text
   Tìm hiểu thêm về Gzip hoặc Broti để tối ưu định dạng text trên site
##### Xác định và ưu tiên load trước các phần LCP
   Nếu có thể xác định được phần nào là LCP content trên site( thường là font chữ, ảnh cover, hero image, hay video). Hãy ưu tiên load trước các phần quan trọng này bằng cấu trúc **<link rel="preload">**
##### Sử dụng lazyload
   Sử dụng Lazyload để load các hình ảnh đang trên khung hình, chỉ khi nào scroll tới thì mới load hình ảnh lên => Giảm thời gian load site
### [FID - Thời gian phản hồi lần tương tác đầu tiên](https://web.dev/optimize-fid/))
#### FID là gì?
FID - First Input Delay chỉ số đo thời gian từ khi người dùng tương tác lần đầu với trang web( nhấn vào 1 CTA, click link, nhập pass...) đến thời điểm mà trình duyệt thực sự phản hồi với hành động tương tác đó.

==Kết quả đo được lấy bất kỳ phần từ nào có thể phản hồi khi người dùng nhấp lần đầu==

#### FID có ý nghĩa gì tới trải nghiệm người dùng?
Chỉ số FID có ý nghĩa quan trọng với các trang đòi hỏi người dùng tương tác như **Đăng nhập, Đăng ký, Điền thông tin**. Khi người dùng điền thông tin cần có phản hồi nhanh lại. 

Nếu trang đích đơn thuần là đọc bài thì chỉ số FID này không cần qua quan tâm.

#### FID thế nào thì gọi là cao?
Chỉ số FID dưới 100mili giây thì được coi là tốt

![[Chi-so-danh-gia-FID-Core-Web-Vitals.png]]

#### Làm sao tối ưu chỉ số FID?
##### Giảm thiểu tác động từ các phần mềm thứ 3
Các phần mềm thứ ba có thể can thiệp vào các action trên site, vì vậy chọn lựa nhà cung cấp nào có tốc độ nhanh, ổn định. Thường xuyên tối ưu, dọn dẹp bớt các code không cần thiết cảu bên thứ 3.
##### Tối ưu các đoạn mã JavaScript
Tối ưu các đoạn Javascript trên site giúp trang load nahnh hơn, response lại nhanh hơn 
##### Sử dụng cache
Sử dụng tính năng cache của browser giúp tăng tốc độ load Javascript từ đó tăng các tương tác. 
### CLS - Điểm số tổng hợp về mức thay đổi bố cục
#### CLS là gì?
CLS - Cummulative layout shift là chỉ số đo lường tổng của tất cả các điểm số riêng lẻ về thay đổi bố cục cho lần thay đổi bố cục không mong muốn xảy ra trong toàn bộ thời gian hoạt động của trang.

Điểm số 0: nghĩa là trang không thay đổi bố cục. Điểm CLS càng cao nghĩa là bố cục được thay đổi ngàng nhiều.
![[Vi-du-ve-CLS-Core-web-Vital.png]]

HÌnh bên trái, bố cục bị thay đổi bất chợt khi load, khiến user có thể click nhầm vào. Hình bên phải có bố cục được khuân vùng rõ, ngay từ đầu rõ ràng, nên khiến user trải nghiệm tốt hơn, các element không tự động xuất hiện.

#### Chỉ số này có ý nghĩa gì với trải nghiệm người dùng?
Nếu cấu trúc thay đổi bất chợt, khiến User thường xuyên click nhầm => trải nghiệm xấu
![[core.png]]
 CLS càng cao, khả năng người dùng click nhầm vào các phần tử không mong muốn càng lớn.
#### Chỉ số CLS như thế nào thì tốt?
CLS = 0 là tốt nhất, > 0.25 là rất tệ
![[Chi-so-danh-gia-CLS.png]]

#### [Cách cải thiện chỉ số CLS](https://web.dev/optimize-cls/)
##### Hạn chế hiển thị các phần tử, thành phần trên website bất chợt.
Khi thiết kế trang web, nên có khoảng riêng cố định dành riêng cho thành phần đó.

Ví dụ: banner quảng cáo nên được thiét kế bên trái màn hình nơi người dùng đã quen thuộc với nó. 
Content nên được đặt lên trên cùng và không nên có các thành phần khác đè lên sau khi load. 

#####  Đảm bảo các phần tử đã có 1 không gian được định sẵn
Sử dụng "set size attribute dimension" cho các media: browser sẽ biết chính xác những thành phần sẽ chiếm vị trí nào, đoạn nào trên page, không thay đổi các thành phần khác khi phần này load xong.
## Các kiểm tra các chỉ số Core Web Vitals
- [### Google Page Spee](https://developers.google.com/speed/pagespeed/insights/?hl=vi)
- Google Search Console
- Chrome Extension: Add on Web vitat
- Chrome DevTools Performance pannel: Trong F12 cso tab Performance => sẽ cho chính xác report
- web.dev/measure
- 

[Core Web Vitals - Update quan trọng nhất của Google 2021 (seongon.com)](https://seongon.com/blog/seo/core-web-vitals.html)
