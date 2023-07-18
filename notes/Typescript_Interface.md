---
title: 'Interface'
date: '2020-01-02'
type: programing 
---

# Typescript Interface


Trong TypeScript, interface chịu trách nhiệm Naming các types. Nó giúp compiler có thể đơn giản check Types, và code cũng rõ ràng hơn. 
Interface có thể dùng được trong các trường hợp dưới đây.

## Property Type
```typescript
interface LabeledValue {
  label: string;
}

function printLabel(labeledObj: LabeledValue) {
  console.log(labeledObj.label);
}

let myObj = { size: 10, label: "Size 10 Object" };
printLabel(myObj);
```
Interface không yêu cầu các properties phải đúng thứ tự như khai báo, chỉ cần đúng tên và type là được. 

### Optional Properites
```typescript
interface SquareConfig {
  color?: string;
  width?: number;
}
```
Các properties trong interface không nhất thiết bắt buộc phải có. Dùng cách này có thể giúp ràng buộc khi sử dụng phải chọn đúng tên giống trong Interface nhưng lại không bắt buộc phải có. Interface còn giúp codesnipper khi develop

### Readonly properties
```typescript
interface Point {
  readonly x: number;
  readonly y: number;
}

let p1: Point = { x: 10, y: 20 };
p1.x = 5; // error!
```
Cho phép tạo ra những biến Immutable. 

## Function Types
Interface còn dùng để tạo template cho function. Định nghĩa các types đầu vào và đầu ra cho function.
```typescript
interface SearchFunc {
  (source: string, subString: string): boolean;
}

let mySearch: SearchFunc;

mySearch = function (source: string, subString: string): boolean {
  let result = source.search(subString);
  return result > -1;
};
```

## Indexable Types
Có thể định nghĩa chính xác Types của **index** sẽ phải truyền vào như thế nào
```typescript
interface NumberDictionary {
  [index: string]: number;
  length: number; // ok, length is a number
  name: string; // error, the type of 'name' is not a subtype of the indexer
Property 'name' of type 'string' is not assignable to string index type 'number'.
}
```
Đoạn code trên thể hiện, tất cả các index là string thì phải trả về number. Do property *name* có index là *name* là 1 string nhưng lại chứa giá trị String nên TypeScript sẽ báo lỗi. 
Muốn chứa giá trị khác thì phải khai báo thêm
```typescript
interface NumberOrStringDictionary {
  [index: string]: number | string;
  length: number; // ok, length is a number
  name: string; // ok, name is a string
}

```

## Class Types
Giống như mọi ngôn ngữ khác, Interface trong TypeScript cũng có thể dùng để định nghĩa method bắt buộc phải có 
```typescript
interface ClockInterface {
  currentTime: Date;
  setTime(d: Date): void;
}

class Clock implements ClockInterface {
  currentTime: Date = new Date();
  setTime(d: Date) {
    this.currentTime = d;
  }
  constructor(h: number, m: number) {}
}

```
## Hybrid Types
Cách để có thể Hybrid thành object mình mong muốn
```typescript
interface Counter {
  (start: number): string;
  interval: number;
  reset(): void;
}

function getCounter(): Counter {
  let counter = function (start: number) {} as Counter;
  counter.interval = 123;
  counter.reset = function () {};
  return counter;
}

let c = getCounter();
c(10);
c.reset();
c.interval = 5.0;
```

---
Tags: [[Typescript Basics]]