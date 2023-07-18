---
type: programing 
---
# Golang Basic Types

## [[Golang String|String]]

## [[Golang Numbers|Numbers]]

Other types
```
var u uint = 7  // uint (unsigned)
var p float32 = 22.7 // 32-bit float

```

## [[Golang Arrays|Arrays]]

## [[Golang Pointers|Pointers]]

## Ép kiểu Type conversions
```
package main

import (
	"fmt"
	"math"
)

func main() {
	var x, y int = 3, 4
	var f float64 = math.Sqrt(float64(x*x + y*y))
	var z uint = uint(f)
	fmt.Println(x, y, z)
}

```


---
Tags: [[Golang]]