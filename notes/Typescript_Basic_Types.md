---
title: 'Basic Types'
date: '2020-01-02'
type: programing 
---

# Typescript Basic Types

## TypeScript hỗ trợ các kiểu cơ bản 
### Boolean
```typescript
let isDone: boolean = false;
```
### Number | BigInt 
```typescript
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
let big: bigint = 100n;

```
### String
```typescript
let color: string = "blue";
let sentence: string = `Hello, my name is ${fullName}.
```

### Array
Các phần tử trong Array có cùng 1 Type
```typescript
let list: number[] = [1, 2, 3];
```
#### Generic Array Type Array`<elementType>`

```typescript
let list: Array<number> = [1, 2, 3];
```
#### Tuple
Các phần tử có thể thuộc nhiều Type khác nhau, nhưng phải được khai báo trước
```typescript
// Declare a tuple type
let x: [string, number];
// Initialize it
x = ["hello", 10]; // OK
// Initialize it incorrectly
x = [10, "hello"]; // Error`
```
### Enum: 
```typescript
enum Color {
  Red,
  Green,
  Blue,
}
let c: Color = Color.Green;
```

### Unknown:
Khi không biết trước được rằng biến sẽ nhận được giá trị kiểu gì thì sẽ sử dụng unknown
```typescript
let notSure: unknown = 4;
notSure = "maybe a string instead";

// OK, definitely a boolean
notSure = false;
```
### any
Giống *unknown* type, *any* khác ở chỗ nó cho truy xuất vào các thuộc tính của biến ngay cả khi nó không tồn tại. 
```typescript
let looselyTyped: any = 4;
// OK, ifItExists might exist at runtime
looselyTyped.ifItExists();
// OK, toFixed exists (but the compiler doesn't check)
looselyTyped.toFixed();

let strictlyTyped: unknown = 4;
strictlyTyped.toFixed();
Object is of type 'unknown'.
```


---
Tags: [[Typescript]]