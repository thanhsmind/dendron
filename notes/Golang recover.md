---
type: programing 
---
# Golang recover là gì? Khi nào dùng recover?

**recover** là 1 hàm tính năng giúp giành lại quyền kiểm soát khi có 1 goroutine bị [[Golang panic]].  ==recover chỉ hữu dụng bên trong hàm defer==. Trong trường hợp bình thường, kết quả hàm recover trả về là nil. Khi chương trình bị panic, hàm recover sẽ trả về reason 

```
package main

import "fmt"

func main() {
    f()
    fmt.Println("Returned normally from f.")
}

func f() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered in f", r)
        }
    }()
    fmt.Println("Calling g.")
    g(0)
    fmt.Println("Returned normally from g.")
}

func g(i int) {
    if i > 3 {
        fmt.Println("Panicking!")
        panic(fmt.Sprintf("%v", i))
    }
    defer fmt.Println("Defer in g", i)
    fmt.Println("Printing in g", i)
    g(i + 1)
}
```

Chương trình phía trên sẽ gọi hàm `panic` khi i > 3. Khi đó chương trình sẽ trả về hàm gọi nó là hàm f(). Hàm f() sẽ gọi hàm `defer`, hàm `defer` sẽ gọi `recover` và  chương trình tiếp tục chạy lại như bình thường.

---
Tags: [[Golang Function]]