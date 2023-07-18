---
title: 'Authentication using an API'
date: '2020-01-02'
type: programing 
---

# Javascript Authentication using an API

![[bobank-authentication.png]]


- **[[PHP Authenticate]]**: Khi login, page gửi username & password về server xử lý. 
- **Authorization**: Khi muốn truy xuất vô resource, trước tiên phải gửi token [[JWT - JSon Web Token]] về xem user đó có quyền để truy cập resource đó hay không.

#### Web Storage and Authorization Header
Thường các ứng dụng xây dựng bằng JavaScript sau khi authenticate thường lưu thông tin token tại Session Storage hoặc Local Storage. 
```javascript
authenticate(login, password)
    .then(function(authentication) {
        window.sessionStorage.setItem('token', authentication.token);
		// localStorage.setItem('token', authentication.token);
		});
```

#### Authorization
Sau khi Authenticate thành công, để truy xuất vào các resource thì cần gửi header `Authorization` tới server.
```javascript
/**
 * @return {Promise}
 */
function getAccounts() {
    return fetch('https://api.bobank.com/accounts', {
        headers: {
            'Authorization': 'Token ' + window.sessionStorage.getItem('token'),
            'Content-Type': 'application/json; charset=utf-8',
            'Accept': 'application/json',
        }
    }).then(function(response) {
        return response.json();
    })
}
```
Lưu ý: `Authorization` header phải được thêm vào trong `Acces-Control-Allow-Headers` trên server.
Example response:
```
HTTP/1.1 200 OK
Content-Type:application/json; charset=utf-8
Access-Control-Allow-Headers: Content-Type,Authorization
Access-Control-Allow-Methods: GET,POST,PUT
Access-Control-Allow-Origin: https://www.bobank.com
[
  { id: 456346436, ... }
]

```

#### Session Cookie Storage
Browser có phương thức lưu trữ nhưng không cho Javascript đọc khi thêm cờ `HttpOnly`. Khi đó, Cookies sẽ tự động được browser gửi tới server. Việc không truy suất được từ JavaScript giúp site ==không bị XSS==. 

```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Headers: Content-Type
Access-Control-Allow-Methods: GET,POST,PUT
Access-Control-Allow-Origin: https://www.bobank.com
Set-Cookie: session=15d38683-a98f-402d-a373-4f81a5549536; path=/; expires=Fri, 06 Nov 2015 08:30:15 GMT; httponly

```

---
Tags: [[Javascript]], [[Authentication]]