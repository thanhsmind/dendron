---
title: 'ES6 Destructuring Assignment'
date: '2020-01-02'
type: programing 
---

# ES6 Destructuring Assignment

*Destructuring assignment* là biểu thức Javascript dùng để lấy ra giá trị của một hay nhiều phần từ trong Array, Object gán cho các biến cho trước.

#### Destructuring Object `{ var_1, var_2} = object;`
```javascript
let iPhone = {  
    model: "iPhone X",
    price: "$1500 USD",
    year: 2017
};

let { model, price, year } = iPhone;

console.log(model); // iPhone
console.log(price); // $1500 USD
console.log(year); // 2017
```
Tên các biến destructuring phải cùng tên với các property trong object 

#### Destructuring Array `[var1, var2] = array; `
```javascript
let topSmartPhones2017 = [
    "Samsung Galaxy S8",
    "Samsung Galaxy S8 Plus",
    "iPhone 7 Plus",
    "Samsung Galaxy Note 8",
    "OnePlus 5"
];

let [first, second, third, forth, fifth ] = topSmartPhones2017;

console.log(first); // Samsung Galaxy S8
console.log(second); // Samsung Galaxy S8 Plus
console.log(third); // iPhone 7 Plus
console.log(forth); // Samsung Galaxy Note 8
console.log(fifth); // OnePlus 5
```


---
Tags:  [[ES6]] - [[ECMAScript 2015]] 