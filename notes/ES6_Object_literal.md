---
title: 'Object literal'
date: '2020-01-02'
type: programing 
---

# ES6 Object literal

*Object Literal* là cú pháp tạo object sử dụng dấu =={}==, bên trong đó là danh sách các property của object.

Phiên bản ECMAScript cũ sẽ khởi tạo object 
```javascript
var name = "John";
var myObj = {
    name: name,
    sayHi: function () {
        console.log("Hi, my nam is " + this.name)
    }
};
```

Cú pháp Object literal trong ES6
1. Những *property có tên trùng với giá trị* bên ngoài như `name:name` thì có thể viết ngắn gọn bằng `name`
2. Method trong object có thể bỏ bớt từ khóa `function`. 
```javascript
var name = "John";
var myObj = {
    name,
    sayHi() {
        console.log("Hi, my nam is " + this.name)
    }
};

myObj.sayHi();
```

---
Tags:  [[ES6]] - [[ECMAScript 2015]] 