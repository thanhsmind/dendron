---
type: programing 
---
# ECMAScript 2020

#### Hot loading modules
```javascript
const baseModulePath = "./modules"; 
const btnBooks = document.getElementById("btnBooks"); 

let bookList = []; 
btnBooks.addEventListener("click", async e => { 
	const bookModule = await 
	import(`${baseModulePath}/books.js`);
	bookList = bookModule.loadList(); 
});

```

 Đoạn code này chỉ được load khi có phát sinh sự kiện `click event`. Thay vì load vào ngay từ đầu.
 
 ---
 - Tags: [[Javascript]]
 - Reference:
 - Related:
	 - [[ES6|ECMAScript 2015]]
	 - [[ECMAScript 2016]]
	 - [[ECMAScript 2017]]
	 