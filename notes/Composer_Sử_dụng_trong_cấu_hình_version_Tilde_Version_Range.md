---
title: 'Sử dụng `~` trong cấu hình version Tilde Version Range `~`'
date: '2020-01-02'
type: programing 
---

# Composer Sử dụng `~` trong cấu hình version Tilde Version Range `~`

Dấu ngã `~` được sử dụng cho cấu hình muốn chỉ số cuối cùng tăng tối đa, nhưng không bao giờ tăng chỉ số kế cuối . Được sử dụng trong các dự án tôn trọng [[Git Sematic Versioning]] . 
	- `~` thường được sử dụng để chỉ [[minor version]] nhỏ nhất mà project phụ thuộc vào. Ví dụ: `~1.2`, với cấu hình này, composer chỉ lấy version `<2.0`. Theo lý thuyết thì version 2.0 không bao giờ compatibility với version nhỏ hơn.
	- `~` cũng được dùng cho chỉ định ***cụ thể  1 phiên bản*** phụ thuộc. Nhưng cho phép thay đổi chỉ số cuối cùng. Ví dụ: `~1.3.2` ==> `>=1.3.2 <1.4.0`
```
"require": {
    // ~ | allows last digit specified to go up
    "vendor/package": "~1.3.2", // >=1.3.2 <1.4.0
    "vendor/package": "~1.3", // >=1.3.0 <2.0.0
}
```

---
Tags: [[Composer]], [[Composer Version Range]]