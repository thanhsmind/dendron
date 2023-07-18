---
title: 'Token based authentication'
date: '2020-01-02'
type: programing 
---

# JWT Token based authentication

### Định nghĩa:
**Token-based authentication** là phương thức xác thực bàng chuỗi mã hóa. Một hệ thống sử dụng **Token-based authentication** cho phép người dùng đăng nhập bằng *username/password* và nhận lại 1 *chuỗi mã token*. **Token** này được sử dụng để xác minh lại quyền truy cập vào tài nguyên mà không cần phải cung cấp lại *username/password*. 

### Tại sao lại sử dụng Token-based authentication
Với cách [[Cookie based authentication]] thông thường, các ứng dụng phải tự lưu lại thông tin để có thể authentication, với thông tin đó họ có thể truy xuất vào tài nguyên một cách thoải mãi và vĩnh viễn. Các ứng dụng muốn cung cấp các quyền truy cập tạm thời, có thời hạn truy cập vào tài nguyên hệ thống rất khó. Việc cung cấp này sẽ dễ dàng hơn nếu sử dụng thông qua hệ thống authenticate không sử dụng password. Vì vậy, **Token-based authentication** là giả pháp tốt cho trường hợp này. **Token-based authentication** thường được sử dụng cho các ứng dụng API đòi hỏi truy suất thông tin từ ngoài vào.

### Cách thực thi 
- [[JWT - JSon Web Token]] JWT - Json Web Token

---
Tags: [[JWT - JSon Web Token]]