---
title: 'constructor function'
date: '2020-01-02'
type: programing 
---

# Typescript constructor function

```javascript
let Greeter = (function () {
  function Greeter(message) {
    this.greeting = message;
  }

  Greeter.prototype.greet = function () {
    return "Hello, " + this.greeting;
  };

  return Greeter;
})();

let greeter;
greeter = new Greeter("world");
console.log(greeter.greet()); // "Hello, world"
```


---
Tags: [[Typescript]]