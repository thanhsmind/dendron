---
type: programing 
---
# Golang panic là gì? Khi nào dùng panic?

Cách xử lý lỗi trong Go thường là sử dụng hàm return và trả về các lỗi trong quá trình chạy. Những lỗi này thường đã được tính toán trước, và có cách xử lý sao cho chương trình vẫn hoạt động bình thường. Nhưng 1 số trường hợp, chương trình không thể chạy tiếp tục nếu gặp tình huống bất thường. Khi đó sử dụng `panic` tương tự như throw Exception của các ngôn ngữ khác. 

### Hệ thống xử lý thế nào khi gặp panic?
 Trong tình huống chương trình không thể tiếp tục chạy do gặp lỗi bất thường. Khi 1 hàm gặp panic, nó lập tức dừng xử lý, tất cả các hàm được đăng ký `defer` sẽ được gọi, và sau đó sẽ được trả về bên gọi. Tiến trình được tiếp tục cho tới khi tất cả các hàm của goroutine hiện tại được trả về, khi đó chương trình sẽ in ra thông báo Panic, cùng với thông tin stack lỗi, và kết thúc.

Khi một hàm `panic` được gọi xử lý thông thường của goroutine sẽ tạm dừng ngay lập tức:
1. Khi 1 chương trình bị pacnic nó ngay lập tức giải phóng stack gọi
2. Điều này tiếp tục khi chương trình bị lỗi và in ra thông tin stack lỗi. hoặc cho tới khi hàm [[Golang recover]] được gọi.



---
Tags: [[Golang Function]] 