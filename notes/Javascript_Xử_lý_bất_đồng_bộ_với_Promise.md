---
title: 'Xử lý bất đồng bộ với Promise'
date: '2020-01-02'
type: programing
---

# Javascript Xử lý bất đồng bộ với Promise

**Promise** là đối tượng đặc biệt dùng cho xử lý bất đồng bộ. Sử dụng **Promise** cho những action không cần kết quả ngay. Với **Promise** kết quả có thể thực hiện theo Action1 -> Action 2 -> ... -> Action n.

#### Cú pháp
```javascript
new Promise(executor);
new Promise(function(resolve, reject){...});
```
Tham số đầu vào khi khởi tạo đối tượng **Promise** là 1 hàm gồm 2 đối số
- **resolve**: hàm *resolve*  sẽ được gọi khi xử lý thành công
- **reject**: hàm *reject* sẽ được gọi khi xử lý thất bại và trả về Error

==executor== sẽ được gọi ngay lập tức trước cả hàm khởi tạo Promise

#### 3 Trạng thái của `Promise`
- *pending*: Chờ xử lý kết thúc, thể hiện thao tác xử lý chưa kết thúc
- *fulfilled*: Trạng thái xử lý thành công. Có thể đính kèm hàm xử lý thông qua hàm `Promise.prototype.then()`.
- *rejected*:  Xử lý thất bại. Đính kèm hàm xử lý lỗi qua `Promise.prototype.catch()`

- https://developer.mozilla.org/vi/docs/Web/JavaScript/Reference/Global_Objects/Promise

---
Tags:  [[Javascript]]
