---
title: 'React: Sử dụng State Hook'
date: '2021-01-19'
type: programing 
---

# ReactJS Sử dụng State Hook

## Cú pháp useState
` const [state, setState] = useState(initialState)`

Ví dụ : 

```javascript

import React, { useState } from 'react'

function Example(){
 // Khai báo một biến state mới, gọi nó là "count" 
  const [count, setCount] = useState(0);
}

```
### Hàm useState làm gì khi được gọi?
- 1 biến chứa state `count` được khai báo. Nó tương tự với việc lưu trữ state trong class component ` this.state = {count: 0}`
- Khi chạy hết hàm này, state `count` sẽ được React lưu lại trong hệ thống store
- Hàm `setState` là function sử dụng để update state `setState(newState);` Nó thay đổi state và re-render lại component.

### Hàm useState nhận tham số gì ?
Hàm `useState` chỉ nhận 1 tham số đầu vào, tham số đó là giá trị khởi tạo ban đầu. Nó có thể là 1 giá trị bất kỳ. 

### Hàm useState trả về cái gì? 
Hàm `useState` trả về 1 cặp giá trị, bao gồm: 
- state hiện tại
- và ==Hàm thay đổi giá trị ===

đây là cú pháp tạo biến mới thường được dùng [[ES6 Destructuring Assignment]]

### Dùng nhiều biến state

```javascript
function ExampleWithManyStates() {
  // Declare multiple state variables!
  const [age, setAge] = useState(42);
  const [fruit, setFruit] = useState('banana');
  const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
```

---
Tags: [[ReactJS]]