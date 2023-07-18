---
title: 'Sử dụng dấu `^` trong cấu hình version Caret Version Range `^`'
date: '2020-01-02'
type: programing
---

# PHP Composer Sử dụng dấu `^` trong cấu hình version Caret Version Range `^`

`^` thường được sử dụng cho các mối phụ thuộc kiểm soát được và tuân thủ chặt chẽ theo [[Git Sematic Versioning]]

*Lưu ý: Với version nhỏ hơn 1 thì nó luôn tăng khá an toàn. `"^0.3.2", // >=0.3.2 <0.4.0 `

```
"require": {
     // ^ | doesn't allow breaking changes (major version fixed - following semver)
    "vendor/package": "^1.3.2", // >=1.3.2 <2.0.0
    "vendor/package": "^0.3.2", // >=0.3.2 <0.4.0 // except if major version is 0
}
```
---
Tags: [[PHP]] - [[Composer]] - [[Composer Version]]