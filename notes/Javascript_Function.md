---
title: 'Understand Javascript Function'
date: '2020-01-02'
type: programing
---

# Javascript Function

2 cách tiếp cận để tạo 1 function trong javascript
```
// Named function
function add(x, y) {
  return x + y;
}

// Anonymous function
let myAdd = function (x, y) {
  return x + y;
};

```

## Named Function 
Được tạo bởi từ khóa `function`

```
function functionName (parameters) {
  // Do stuff here
}
```

với Named Function, function sẽ được tự động đẩy lên trên khi nó được sử dụng [[Hoisting]]. Hoàn toàn có thể gọi 
```
function sayHello () {
  console.log('Hello world!')
}
sayHello()
```
hoặc
```
// This is automatically converted to the above code
sayHello()
function sayHello () {
  console.log('Hello world!')
}
```
## Anonymous function
Được khởi tạo bởi function expression
```
const sayHello = function () {
  console.log('This is declared with a function expression!')
}

sayHello () // Error, sayHello is not defined
const sayHello = function () {
  console.log('this is a function!')
}
```

## Named Function VS Anonymours Function
- Named Function: có thể dùng với từ khóa `new` để tạo thành 1 object. Mọi Named Function là 1 object
- Named Function: Dễ debug, và được lưu trong memory và có khả năng [[Hoisting]] 
- Anonymours Function: Được tạo ra khi runtime. có tác dụng tạo ra 1 ==function scope== khi xử lý các variable.

---
Tags: [[Javascript]]