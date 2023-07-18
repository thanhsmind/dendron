---
title: 'Generic in TypeScript'
date: '2020-01-02'
type: programing 
---

# TypeScript Generic

**Generic** là một kỹ thuật giúp sử dụng lại code rất nhiều. Nó đưa ra concept Type chung chung, cùng sử dụng lại được các function đã viết lại giữ được thông tin của Type khi đưa vào. 

## Cú pháp
#### Type Varable
```typescript
function identity<T>(arg: T): T {
  return arg;
}

// use

let output = identity<string>("myString");
//       ^ = let output: string
```

#### Generic Types
```typescript
function identity<T>(arg: T): T {
  return arg;
}

let myIdentity: <T>(arg: T) => T = identity;
```


---
Tags: [[Typescript Basics]]
