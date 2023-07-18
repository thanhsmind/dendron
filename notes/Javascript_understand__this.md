---
title: 'Understand Javascript `this`'
date: '2020-01-02'
type: programing 
---

# Javascript understand  `this`

### Cách Javascript gọi 1 *func*
Cách mà 1 function trong javascript được gọi là thông qua method `call`. 
```javascript
function hello(thing){
	console.log(this+" say hello "+ thing);
}

// mỗi 1 'function' trong javascript là 1 object
// Cách gọi sâu bên trong của javascript là sử dụng method 'call'
hello.call(undefined, "Thanhnp");

```

==Function.prototype.call(thisArg[, arg1, [,arg2,...]])== [ES5](http://es5.github.io/[[x15]].3.4.4)
Khi method `call` được gọi trong 1 object *func* với các tham số *thisArg* và optional các đối số *arg1*, *arg2*. Thì các bước sau sẽ được thực hiện:
1. Các đối số được để trong List (argList)
2. Tham số đầu tiên của method `call` là *thisValue*
3. `this` sẽ có giá trị là `thisValue`, và argList là danh sách các tham số
4. nếu `thisValue` có giá trị là **undefined** hoặc **null** thì `thisValue` sẽ được thay thế bằng giá trị ==global object==

### Cách gọi 1 func đơn 
sử dụng method `call` khiến việc gọi 1 hàm khá rườm rà và dài. Javascript cho gọi ngắn hơn.

```javascript
function hello(thing) {
  console.log("Hello " + thing);
}

// this:
hello("world")

// desugars to:
hello.call(undefined, "world");

```
Khi hàm `hello("world")` được gọi. Các mà core javascript sẽ gọi sẽ chuyển thành
```javascript
hello.call(undefined, "world");
```
khi đó `thisArg = undefined;` => `this = thisArg=global Object`

==fn(...args) tương đương fn.call(window [ES5-strict: undefined], ...args)==

### Gọi 1 method trong 1 function
Khi gọi 1 method được gắn bên trong 1 object `func`. Core javasript sẽ điền object đó vào trong biến `thisArg`
```javascript
var person = {
  name: "Brendan Eich",
  hello: function(thing) {
    console.log(this + " says hello " + thing);
  }
}

// this:
person.hello("world")

// desugars to this:
person.hello.call(person, "world");

```

Nếu 1 function là độc lập và nó được gắn vào bên trong 1 object. Thì chi tiết cách gọi sẽ như vậy

```javascript
function hello(thing) {
  console.log(this + " says hello " + thing);
}

person = { name: "Brendan Eich" }
person.hello = hello;

person.hello("world") // still desugars to person.hello.call(person, "world")

hello("world") // hello([object DOMWindow], "world");
```

### `this` trong arrow function
Với arrow function, `this` có ý nghĩa trong ngữ cảnh bọc hàm arrow function.
```javascript
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // |this| ở đây trỏ tới đối tượng person
  }, 1000);
}

var p = new Person();

```

1 ví dụ khác
```javascript
let deck = {
  suits: ["hearts", "spades", "clubs", "diamonds"],
  cards: Array(52),
  createCardPicker: function () {
    return function () {
      let pickedCard = Math.floor(Math.random() * 52);
      let pickedSuit = Math.floor(pickedCard / 13);

      return { suit: this.suits[pickedSuit], card: pickedCard % 13 };
    };
  },
};

let cardPicker = deck.createCardPicker();
let pickedCard = cardPicker();

alert("card: " + pickedCard.card + " of " + pickedCard.suit);

```

Đoạn code trên khi chạy sẽ bị lỗi. `return { suit: this.suits[pickedSuit], card: pickedCard % 13 };` có giá trị là window do khi gọi `let cardPicker = deck.createCardPicker(); => let cardPicker = deck.createCardPicker.call(undefined);`

Muốn this hiểu là `deck` thì có thể sử dụng arrow function. **arrow function** hiểu this nằm trong scope code chứa nó chứ không phải tại scope chạy function
```javascript
let deck = {
  suits: ["hearts", "spades", "clubs", "diamonds"],
  cards: Array(52),
  createCardPicker: function () {
    // NOTE: the line below is now an arrow function, allowing us to capture 'this' right here
    return () => {
      let pickedCard = Math.floor(Math.random() * 52);
      let pickedSuit = Math.floor(pickedCard / 13);

      return { suit: this.suits[pickedSuit], card: pickedCard % 13 };
    };
  },
};

let cardPicker = deck.createCardPicker();
let pickedCard = cardPicker();

alert("card: " + pickedCard.card + " of " + pickedCard.suit);

```

---
Tags: [[Javascript]]