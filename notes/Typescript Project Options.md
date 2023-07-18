---
title: 'Project Options'
date: '2020-01-02'
type: programing 
---

# Typescript Project Options

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
	// allow import file with extension *.js*, *.ts, 
    "allowJs": true,
	// enable raise error when check files *.js. Effect when allowJs:true
	"checkJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react"
  },
  // Load all files by glob pattern
  "include": [
    "src"
  ]
}

```


#### Allow JS - allowJs
Cho phép import file Javascript vào trong project Typescript. 
```javascript
// @filenaem: card.js
export const defaultCardDeck = "Heart";
```

Khi 
```json
{
  "compilerOptions": {
   	...
    "allowJs": false,
  }
}
```
import vào file Typescript sẽ bị báo lỗi 
```javascript
import { defaultCardDeck } from ".card";

console.log(defautlCardDeck);
```
Khi `"allowJs": true,` sẽ không bị báo lỗi. 

`allowJs` thường được dùng khi project JS và đang dần chuyển qua Typescript Files.

#### Check JS - checkJs
Khi chạy song song 2 loại JS & TS trong cùng 1 project với `allowJs:true`. Khi `checkJs: true` sẽ bật lên chế độ báo lỗi trong tất cả các file Javascript. Tương đương với add `@ts-check` vào tất cả các file Javascript trong project.


#### JSX - jsx
2 bước để sử dụng React với Typescript
1. File name sử dụng React có extension là *.tsx*
2. Enable jsx option `jsx: true`

**jsx option** có 3 modes:

|Mode|Input|Output|Output File Extension|
|---|---|---|---|
|preserve|`<div />`|`<div />`|.jsx|
|react|`<div />`|React.createElement("div") |.js|
|react-native| `<div />`|`<div />`|.js|

mode này có ảnh hưởng khi emit state - type checking không ảnh hưởng tới.

#### target
Khi build file Typescript ra thành Javascript thì nó sẽ export JS theo chuẩn gì es6, hay es5.



https://www.typescriptlang.org/tsconfig#jsx


---
Tags: [[Typescript]] 