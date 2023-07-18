---
title: 'Rest Parameter'
date: '2020-01-02'
type: programing 
---

# ES6 Rest Parameter

Rest parameter trong [[ES6]] giúp có thể định nghĩa 1 hàm có một số lượng tham số thay đổi tùy ý. Rest parameter nhóm tất cả các đối số truyền vào thành 1  array.

### Cú pháp Rest Parameter
Rest parameter thường thông qua 3 dấu chấm `...`
```javascript
function f(param1, param2, ...rest_parameter){
	//...
}

```
Example:
```javascript
function sumNumbers(...numbers){
	console.log(numbers);
}

sumNumbers(2,3); // [2, 3]
sumNumbers(2,3,100); // [2,3, 100]
```

---
Tags:  [[ES6]] - [[ECMAScript 2015]] 