---
title: 'tsconfig.json References'
date: '2020-01-02'
type: programing 
---

# Typescritpt tsconfig.json References

`tsconfig.json` là file chứa config của project Typescript. File này được đặt tại thư mục gốc **root** của project Typescript. 

## Root Fields
Các fields config nằm tại root của file Tsconfig

### File Inclusion
Những cấu hình giúp Typescript có thể lọc đúng file để sử dụng cho dự án.
##### Exclude -exclude
**Default: ["node_modules", "bower_components", "jspm_packages"],**
Chỉ định rõ các files hay pattern dẫn đến các files sẽ bị bỏ qua khi *include* option được thực hiện. 

*Lưu ý*: Các file bị loại bỏ với option *exclude* vẫn là 1 phần của codebase, và vẫn có thể import trong code khi sử dụng statement *import*.

##### Extends - extends
**Default: false**
Giá trị của *extends* là 1 string, nó chứa đường dẫn tới 1 file config khác để kết thừa từ đó. 
File config được chỉ định *extends* sẽ được load trước, các cấu hình trong file đó sẽ được *overridden* bởi những cấu hình sau. 

Example:
configs/base.json:
```javascript
# configs/base.json:
{
  "compilerOptions": {
    "noImplicitAny": true,
    "strictNullChecks": true
  }
}
```
tsconfig.json:
```javascript
{
  "extends": "./configs/base",
  "files": ["main.ts", "supplemental.ts"]
}
```
tsconfig.nostrictnull.json:
```javascript
{
  "extends": "./tsconfig",
  "compilerOptions": {
    "strictNullChecks": false
  }
}
```

##### Files -files
**Default: false**
Xác định các files sẽ được include vào trong project typescript. Nếu files không tìm thấy thì sẽ báo lỗi. Thường sử dụng cho project ít files.
```javascript
{
  "compilerOptions": {},
  "files": [
    "core.ts",
    "sys.ts",
    "types.ts",
    "scanner.ts",
    "parser.ts",
    "utilities.ts",
    "binder.ts",
    "checker.ts",
    "tsc.ts"
  ]
}
```
##### Include - include
**Default: false**

```json
{
  "include": ["src/**/*", "tests/**/*"]
}
```

*include*, *exclude* hỗ trợ wildcard.
- * matches zero or more characters (excluding directory separators)
- ? matches any one character (excluding directory separators)
- `**/` matches any directory nested to any level
Nếu glob pattern không chỉ định rõ file extension, thì chỉ những file có extensions default được hỗ trợ ( .ts, .tsx, và .d.ts, thêm .js và .jsx nếu flag *allowJs* được set to true).

##### References - references
**Default: false**
[[Typescript Project References]] là cách cấu trúc của project Typescript.

##### Type Acquisition - typeAcquisition
**Default: false**
Thay đổi @types mặc định của Typescript project. Mặc đinh project typescript sử dụng *DefinitelyTyped* 
```json
{
  "typeAcquisition": {
    "enable": false
  }
}
```
```json
{
  "typeAcquisition": {
    "exclude": ["jquery"]
  }
}
Default:

```

## Compiler Options
- [[Typescript Project Options]]: Project Options
- [[Typescript Strict Checks]]: Strict Checks
- [[Typescript Module Resolution]]: Module Resolution
- [[Typescript Source Maps]]: Source Maps
- [[Typescript Linter Checks]]: Linter Checks
- [[Typescript Experimental]]: Experimental



---
Tags: [[Typescript]] 