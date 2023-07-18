---
type: programing 
---
# Golang Modules

*module* là 1 tập hợp của nhiều packages có liên quan với nhau, và released cùng nhau. File `go.mod` dùng để khai báo đường dẫn tới module, nó dùng để import prefix path tới các packages trong module. module chứa các packages trong thư mục chứa file `go.mod`. 1 Repository thường chỉ chứa 1 module. 

==Chú ý==: Không cần phải publish code lên remote repository trước khi build nó. Mỗi module có thể được định nghĩa dưới local mà không nhất thiết phải có remote repository. 
*module's path* không chỉ cung cấp *import path prefix* tới packages mà nó chứa, mà còn có ý nghĩa chỉ cho go  biết nên download nó ở đâu.
### Setup 1 module.

```sh
$ mkdir auth
$ cd auth
$ go mod init example-domain.com/user/auth
# go: creating new go.mod: module  example-domain.com/user/auth
$ cat mod.mod

module example-domain.com/user/auth

go 1.16 
#( version go when build)
$
```

Đoạn code trên mô tả cách tạo 1 module. với tên là auth. *import path*: là example-domain.com/user/auth

---
Tags: [[Golang]]
