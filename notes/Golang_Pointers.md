---
type: programing 
---
# Golang Pointers 
**Pointer** giữ địa chỉ của 1 giá trị. 

[Pointer](https://tour.golang.org/moretypes/1)
type *T là 1 pointer của T value
```
package main

import "fmt"

func main() {
	var p *int
	i:=42
	p=&i
	
	fmt.Println(p)
	fmt.Println(*p)
}


// output
// 0xc000018050
// 42

```

---
Tags:  [[Golang Basic Types]]