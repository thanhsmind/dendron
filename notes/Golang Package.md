---
title: 'Package'
date: '2020-01-02'
type: programing 
---

# Golang Package


### Package trong Golang là gì?
Chương trình Go được tổ chức trong những *packages*. Một *package* là 1 tập hợp các file code ở trong cùng thư mục. 
- Functions, types, varables định nghĩa trong file sẽ được truy xuất bởi các file trong cùng 1 package
### Cấu trúc Package
```
$GOPATH
   - src 
     - github.com
	 	- package-group
			- bar/   // go code in package bar
				x.go
   - bin/
   		quux 		// installed command
   - pkg
     - linux_amd64/
	 		foo/
				bar.a 	// installed package object

```

### Process Build Packages

Khi build packages, **Golang** sẽ tìm code trong 2 thư mục
- $GOROOT/src
- $GOPATH/src

#### Build a Custom Package
`go build github.com/package-group/package-name` 

#### Install a Custom Package
`go install github.com/package-group/package-name`

==Lưu ý==: Khi build chương trình chính. các packages chưa được install trước đó nhưng được import vào sẽ được tự động install vào.

 ---
 Tags: [[Golang]]


