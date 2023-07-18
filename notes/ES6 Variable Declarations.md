---
title: 'Variable Declarations'
date: '2020-01-02'
type: programing 
---

# ES6 Variable Declarations 

Có 3 từ khóa trong javascript dùng để khai báo 1 biến `var`, `let`, `const`

## `var`
`var` là từ khóa phổ biến dùng để khai báo 1 biến trong javascript. Biến được khai báo bằng `var` có hiệu lực trong function mà biến đó được khai báo ==function scope==

```
for (var i = 0; i < 10; i++) {
  setTimeout(function () {
    console.log(i);
  }, 100 * i);
}

Result:
10
10
10
10
10
10
10
10
10
10
```

Vấn đề của `var` 
```
for (var i = 0; i < 5; i++) {
	console.debug(i);
	for (var i = 20; i < 25; i++) {
	  console.debug(i);
	}
}
Result: 
0
20
21
22
23
24
```

Kết quả khác hoàn toàn kết quả chúng ta mong đợi
```
Expect Result:

0
20
21
22
23
24

1
20
21
22
23
24
...
4
20
21
22
23
24

```

Lý do bởi scope khai báo của biến `i`. do `i` được khai báo bởi từ khóa `var` nên nó có scope từ vòng for đầu tiên trở xuống. Thay đổi giá trị i trong vòng for sẽ làm thay đổi giá trị của `i`. Dẫn đến kết quả sai.

```
for (var i = 0; i < 10; i++) {
  setTimeout(function () {
    console.log(i);
  }, 100 * i);
}
Result 
10
10
...
10

```


## `let`
Từ khóa `let` dùng để giải quyết các vấn đề mà khai báo biến bằng `var` gặp phải. Scope của `let` là ==Block Scope==. Biến được khởi tạo bằng `let` chỉ có hiệu lực trong =={}== mà nó khai báo 
```
for (let i = 0; i < 5; i++) {
	console.debug(i);
	for (let i = 20; i < 25; i++) {
	  console.debug(i);
	}
}
Result: 
0
20
21
22
23
24

1
20
21
22
23
24
...
4
20
21
22
23
24
```

```
for (let i = 0; i < 10; i++) {
  setTimeout(function () {
    console.log(i);
  }, 100 * i);
}
Result 
0
1
2
...
9

```
## `const`
`const` là một mức cao hơn của `let`. Biến được khởi tạo bằng từ khóa này sẽ không thể thay đổi được giá trị của nó


---
Tags: [[ES6]] - [[ECMAScript 2015]] 