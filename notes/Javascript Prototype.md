---
title: 'Prototype in Javascript'
date: '2020-01-02'
type: programing
---

# Javascript Prototype

Javasript là một dynamic ngôn ngữ. Chúng ta có thể thêm properties vào 1 object mọi lúc. 
```javascript
function Student() {
    this.name = 'John';
    this.gender = 'Male';
}

var studObj1 = new Student();
studObj1.age = 15;
alert(studObj1.age); // 15

var studObj2 = new Student();
alert(studObj2.age); // undefined
```
Ví dụ trên chỉ rõ rằng, khi thêm 1 property vào 1 instance thì các instance khác sẽ không được thêm vào. Vậy muốn thêm property đó vào tất cả các instance khác thì phải làm sao?

**Prototype** là 1 object được liên kết mặc định với tất cả các function hay object 
![[prototype-associate-default-2-function-object.png]]

Làm sao để truy xuất vào object Prototype 
![[how-to-access-object-prototype.png]]

```javascript
function Student() {
    this.name = 'John';
    this.gender = 'M';
}

var studObj = new Student();

console.log(Student.prototype); // object
console.log(studObj.prototype); // undefined
console.log(studObj.__proto__); // object

console.log(typeof Student.prototype); // object
console.log(typeof studObj.__proto__); // object

console.log(Student.prototype === studObj.__proto__ ); // true
```

Object & function sử dụng `Object.prototype` để truy xuất vào prototype object
Instance thì truy suất thông qua `__proto__` .


---
Tags: [[Javascript]]