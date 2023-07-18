---
type: programing 
---
# Golang defer là gì? Tại sao dùng defer?
Tất cả các lệnh đặt sau Từ khóa **defer** sẽ được thực thi sau khi hàm chứa defer kết thúc. Nó thường dùng để đóng connection hay đóng file. 

```
package main

import "fmt"
func Hello() { 
	defer fmt.Println("World")
	fmt.Println("Hello") 
} 
func main() { 
	fmt.Println("Say") 
	Hello() 
}
```

#### defer được chạy khi nào?
Khi chương trình chạy tới lệnh defer, nó sẽ bỏ qua và chạy các dòng lệnh tiếp theo cho tới khi kết thúc hàm chứa nó. Thì lệnh defer sẽ được chạy. Những trường hợp thường sử dụng defer.
- đóng file cho đỡ quên khi mở
- đóng connection kết nối 
- xử lý các exception nếu có

```
package main

func main() { 
	db, err := leveldb.OpenFile("/db/data", nil) 
	defer db.Close() 
	// Do thing A ... 
	// Do thing B ... 
}
```
### Thứ tự chạy của defer như thế nào?
Nếu nhiều lệnh `defer` được chạy trong hàm. Go sẽ xử lý bằng cơ chế Stack, ==Lệnh nào gọi trước thì chạy trước== 

```
package main

import "fmt"

func main() { 
	fmt.Println("counting") 
	for i := 0; i < 10; i++ { 
		defer fmt.Println(i) 
	} 
	fmt.Println("done") 
}

```

---
Tags: [[Golang Function]]
