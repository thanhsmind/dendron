---
type: programing
---
# JavaScript String Padding

[[ECMAScript 2017]] thêm 2 method mới cho String
- `padStart`: Thêm padding vào đầu String
- `padEnd`: Thêm padding vào cuối String

### Example
```javascript 

let str = "5";
str = str.padStart(4,0);
// result is 0005
//=======================//
let str = "5";
str = str.padEnd(4,0);
// result is 5000
```