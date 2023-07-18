---
title: 'Typescript'
date: '2020-01-02'
type: programing 
---

# [[Typescript]]

- [[Typescript Basics]]
- [[TypeScript with ReactJS]]
## Cấu trúc project Typescript
```
my-app/
|___ .gitignore 
|___ node_modules/
|--- package.json
|___ public
|___ |___ favicon.ico
|___ |___ index.html
|___ |___ manifest.json
|___ README.md
|___ src
|___ |___ App.css
|___ |___ App.test.tsx
|___ |___ App.tsx
|___ |___ index.css
|___ |___ index.tsx
|___ |___ logo.svg
|___ tsconfig.json
|___ yarn.lock

```
Trong đó :
- **tsconfig.json** [[Typescritpt tsconfig-json References]]: Khai báo các tùy chọn cho biên dịch từ *Typescript* sang *Javascript*
- **tslint.json**: Khai báo các cài đặt được sử dụng bởi [[TSLint]] ( công cụ kiểm tra code typescript).
- **public**: Thư mục chứa những file tĩnh như index.html.
- **src**: Thư mục chứa code giao diện, logic của ứng dụng. Bao gồm các *components* viết bằng Typescript và CSS file. Trong thư mục này *index.js* sẽ thay thế bằng *index.tsx* 

### Những điểm lưu ý khi dùng Typescript trong project ReactJS
#### .tsx thay vì dùng .jsx
Typescript có đuôi mở rộng là `.ts` nên file dùng để khai báo phần tử hoặc component thường để trong file `.tsx`.  Để sử dụng option này thì phải cấu hình cho trình biên dịch biết
```json
// tsconfig.json
{
  "compilerOptions": {
    "jsx": "react"
  }
}
```


- [[ReactJS Component]]: Defind Reactjs Component
- [[Typescript support ReactJs]]: Typescript support Reactjs
- [[Typescript Project References]]: Typescript Project References
- [[Typescript Babel work together]]: How Typescript & Babel work together?



https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html


