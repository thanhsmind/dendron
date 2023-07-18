---
title: 'Import & Export'
date: '2020-01-02'
type: programing 
---

# ES6 Import & Export

ES6 giới thiệu 2 từ khóa mới `import`, `export` hỗ trợ include code theo từng module.
==Lưu ý: `export` & `import` chỉ hỗ trợ ở một vài phiên bản mới nhất.

#### `export`
Câu lệnh `export` dùng để xuất ra một hoặc nhiều  module. 
```javascript
let sayHello = function (name) {
    console.log("Xin chào! Tên tôi là " + name);
}

let sayGoodbye = function () {
    console.log("Chào tạm biệt!");
}
export { sayHello, sayGoodbye };
```

#### `import`
Dùng `import` để nhập vào module từ file lib. 
`import { sayHello } from 'say_hello.js';`
tùy biến tên biến khi import module
`import { sayHello as sayHelloFunction } from 'say_hello.js'; `

---
Tags:  [[ES6]] - [[ECMAScript 2015]] 