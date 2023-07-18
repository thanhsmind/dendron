---
title: 'Literal Types'
date: '2020-01-02'
type: programing 
---

# Typescript Literal Types

## Literal là gì?
**Literal** là 1 giá trị  thường được gán vào 1 biến. `let hello="Đây là 1iteral";`.  **Literal** có thể là string, number, boolean hay bất cứ giá trị nguyên thủy nào. 

## Literal dùng khi nào? 
Trong khi lập trình, có 1 số function chung ta cần truyền vào một vài giá trị có types nguyên thủy nhưng chỉ chấp nhận một số giá trị chứ không phải tất cả. Ví dụ như 
```typescript
type Easing = "ease-in" | "ease-out" | "ease-in-out";

class UIElement {
  animate(dx: number, dy: number, easing: Easing) {
    if (easing === "ease-in") {
      // ...
    } else if (easing === "ease-out") {
    } else if (easing === "ease-in-out") {
    } else {
      // It's possible that someone could reach this
      // by ignoring your types though.
    }
  }
}

let button = new UIElement();
button.animate(0, 0, "ease-in");
button.animate(0, 0, "uneasy");
Argument of type '"uneasy"' is not assignable to parameter of type 'Easing'.
```
như ví dụ trên. Function `animate` có param là easing chỉ muốn nhận một trong các giá trị như `"ease-in" | "ease-out" | "ease-in-out"`. Tất cả các giá trị này đều có type là string. Như vậy muốn compiler có thể báo lỗi khi truyền sai giá trị vào là rất khó. Nhưng điều này lại dễ dàng với Literal Type

## Cú pháp
`type Tên-Literal=type= Giá trị 1 | Giá trị 2 | ... | Giá trị N;`

## Các loại Literal Types

### Numeric Literal Types
```typescript
function rollDice(): 1 | 2 | 3 | 4 | 5 | 6 {
  return (Math.floor(Math.random() * 6) + 1) as 1 | 2 | 3 | 4 | 5 | 6;
}

interface MapConfig {
  lng: number;
  lat: number;
  tileSize: 8 | 16 | 32;
}

setupMap({ lng: -73.935242, lat: 40.73061, tileSize: 16 });

```

### Boolean Literal Types
```typescript
interface ValidationSuccess {
  isValid: true;
  reason: null;
};

interface ValidationFailure {
  isValid: false;
  reason: string;
};

type ValidationResult =
  | ValidationSuccess
  | ValidationFailure;
```


---
Tags: [[TypeScript Types]]
Reference:
Related: