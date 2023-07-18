---
title: 'Spread Operator'
date: '2020-01-02'
type: programing 
---

# ES6 Spread Operator

*Spread Operator* có cú pháp giống với *rest parameter* nhưng có ý nghĩa khác nhau. *spread operator* được sử dụng trong các câu lệnh, biểu thức, hoặc khi gọi hàm. 

#### Sử dụng với Array
##### Concatenate Array
```javascript
let arr_1 = [1, 2, 3];
let arr_2 = [4, 5, 6];

arr_3 = [...arr_1, ...arr_2];

console.log(arr_3); // [1, 2, 3, 4, 5, 6]
```
#####  Gộp với giá trị khác
```javascript
var numbers = [1, 2, 3]; 
result = ["Car", ...numbers, "Motobike"];

console.log(result); // ["Car", 1, 2, 3, "Motobike"]
```

#### Sử dụng với Object
#####  Copy Object
```javascript
var obj_1 = {name: "ECMAScript"};

var cloned_obj = {...obj_1};
console.log(cloned_obj);
```
#####  Gộp Object
```javascript
var obj_1 = { name: 'ECMAScript' };
var obj_2 = { year: 2015 };

var cloned_obj = { ...obj_1, ...obj_2 };
console.log(cloned_obj); // { name: 'ECMAScript' }
// {name: "ECMAScript", year: 2015}

```

#### Sử dụng với Function
```javascript
function myFn (param_1, param_2, param_3, param_4, param_5) {
}
var args = [2, 3, 4];
myFn(1, ...args, 5);
```

---
Tags: [[ES6]] - [[ECMAScript 2015]] 