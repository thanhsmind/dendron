---
type: programing
---
# JavaScript Object Entries

[[ECMAScript 2017]] thêm vào method mới  cho `Object` là `Object.entries`
method này sẽ trả về 1 ary 
### Example
```javascript
const object1 = {
  a: 'somestring',
  b: 42
};

for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

// expected output:
// "a: somestring"
// "b: 42">)
```


