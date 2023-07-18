---
type: programing 
---
# Golang Pointer

### Những điểm khác nhau  Pointer Go vs C++
1. Không thực hiện được phép tính toán học[[Pointer Arithmetic]] trên con trỏ trong Go. Không thể thực hiện 
	```go
		var ptr *int
		ptr++
	```
	trong go. Go không thể thay đổi địa chỉ của pointer trừ khi bạn gán 1 địa chỉ khác cho nó.
2.   Không có [[Array-Pointer Duality]] trong Go.


---
 Tags: [[Golang Basic Types]]