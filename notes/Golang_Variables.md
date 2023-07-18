---
type: programing 
---
# Golang Variables
Khai báo biến thông thường
```
var msg string
msg = "Hello"
```
Khai báo ngắn
```
msg :="Hello"
```

Hằng số Const

```
 const Phi = 1.618
```

Khai báo nhiều biến cùng types
```
package main

import (
	"fmt"
)

func main() {
	var x, y int = 3, 4
	
	fmt.Println(x, y)
}
```

---
Tags: [[Golang]]