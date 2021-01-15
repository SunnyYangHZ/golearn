# 1.变量

## 1. 变量是什么

变量指定了某存储单元的名称，该存储单元会存储特定类型的值，在go语言语法中，用于声明变量的方法有多种。

### 1.1  声明单个变量

**var name type ** 是声明单个变量的语法。

```go
package main
import "fmt"
func main(){
    var s int //变量声明
    fmt.Println("this is ",s)
}
```

在上述程序中，**var s int**声明了一个int类型变量，名字为s，此时我们并没有为这个变量赋值，go会自动将其初始化为0值。

下面程序我们将为变量赋值

```go
package main
import "fmt"
func main(){
    var s int
    s=1
    fmt.Println("the s is ",s)
    s=5
    fmt.Println("the s is",s)
}
```

### 1.2 声明变量并初始化

语法:"**var name type=初始化值**"用于对变量的初始化

```go
package main
import "fmt"
func main(){
    var s int=2
    fmt.Println("the s is",s)
}
```

### 1.3 类型推断

当变量有初始值时，go语言语法会根据初始值进行推断数据类型，在此过程中可以省略type。

即：var name=初始值，go语法根据初始值推断变量类型。

```go
package main
import "fmt"
func main(){
	var s=2
	fmt.Println("the s is",s)
}
```

### 1.4 声明多个变量

go语言语法支持同时声明多个变量。

语法如：**var name1，name2 type=初始值1，初始值2**

```go
package main
import "fmt"
func main(){
	var s1,s2 int=1,2
	fmt.Println("the s1 is",s1,"the s2 is",s2)
}
```

在某些情况下，我们可能会在**一个语句**中声明不同类型的变量，语法如下：

```go
var (
s1=初始值1，
s2=初始值2
）
```

即在程序中表示如下：

```go
package main
import "fmt"
func main(){
	var(
		s1="hello"
		s2=6
		s3 int
	)
	fmt.Println("s1",s1,"s2",s2,"s3",s3)
}
```

### 1.5 简短声明

go语言支持一种声明变量的简洁形式，即使用**:=** 来表示.

语法为：**name:=初始值**

```go
package main
import "fmt"
func main(){
	s1,s2:="hello",6
	fmt.Println("s1",s1,"s2",s2)
}
```

**注：** 在使用简短声明中，每个变量都要有初始值，否则将会返回错误信息。

# 2.类型

## 2.1 基本类型

- bool
- 数字类型
  - int8
  - int16
  - int32
  - int64
  - int
  - uint8
  - uint16
  - uint32
  - uint64
  - uint
  - float32
  - float64
  - byte
  - rune
- string

## 2.2 bool型

bool类型表示一个布尔值，为true或者false。

```go
package main
import "fmt"
func main(){
    a:=true
    b:=false
    fmt.Println("a:",a,"b",b)
    c:=a&&b
    fmt.Println("c:",c)
    d:=a||b
    fmt.Println("d:",d)
}
```

## 2.3 有符号整型

- int8

  表示8位有符号整型，范围为-128~127。

- int16

  表示16位有符号整型，范围为-32768~32767。

- int32

  表示32位有符号整型，范围为-2147483648~2147483647。

- int64

  表示64位有符号整型，范围为-9223372036854775808～9223372036854775807。

- int

  根据平台不同，所表示的整型位数不同。大小范围为在32位系统下位int32范围，64位系统下位int64范围。

  ```go
  package main
  import "fmt"
  func main(){
      var a int=5
      b:=6
      fmt.Println("value of a is",a,"and b is",b)
  }
  ```

  如果想要输出变量的类型和字节大小，则：

  ```go
  package main
  import(
  	"fmt"
  	"unsafe"
  )
  func main(){
      var a int=5
      b:=6
      fmt.Println("value of a is ",a,"and b is",b)
      fmt.Printf("type of a is %T,size of a is %d",a,unsafe.Sizeof(a))
      fmt.Printf("\ntype of b is %T,size of b is %d",b,unsafe.Sizeof(b))
  }
  ```

  其中说明符%T用于打印类型，%d用于打印字节大小。

## 2.4 无符号类型

- uint8

  表示8位无符号整型，范围为0~255。

- uint16

  表示16位无符号整型。范围为0~65535。

- uint32

  表示32位无符号整型，范围为0～4294967295。

- uint64

  表示64位无符号整型，范围为0～18446744073709551615。

- uint

  平台不同，表示位数不同，范围为在32位系统下是uint32，64位系统是uint64位。



## 2.5浮点型

- float32

  32位浮点数

- float64

  64位浮点数

```go
package main
import "fmt"
func main(){
    a,b:=3.14,2.56
    fmt.Printf("type of a %T b %T\n",a,b)
    sum:=a+b
    diff:=a-b
    fmt.Println("sum",sum,"diff",diff)
    no1,no2:=5,6
    fmt.Println("sum",no1+no2,"diff",no1-no2)
}
```

## 2.6 复数类型

- complex64

  实部和虚部都是float32类型的复数

- complex128

  实部和虚部都是float64类型的复数

内建函数complex用于创建一个包含实部和虚部的复数，函数定义如下：

```go
func complex(r,i FloatType)ComplexType
```

该函数的参数分别是实部和虚部，并返回一个复数类型。实部和虚部应该是相同类型，也就是float32或float64.如果实部和虚部都是float32类型，则函数会返回一个complex64类型的复数，如果实部和虚部都是float64类型，则函数会返回一个complex128类型的复数。

同时还可以用简短的语法来创建复数：

```go
c:=5+6i
```

```go
package main
import "fmt"
func main(){
    c1:=complex(5,6)
    c2:=7+8i
    cadd:=c1+c2
    fmt.Println("sum:",cadd)
    cmu1:=c1*c2
    fmt.Println("product:",cmu1)
}
```

## 2.7 其他数字类型

- byte

  uint8的别名

- rune

  int32的别名

## 2.8 string类型

在 Golang 中，字符串是字节的集合。

```go
package main

import (  
    "fmt"
)

func main() {  
    first := "Naveen"
    last := "Ramanathan"
    name := first +" "+ last
    fmt.Println("My name is",name)
}
```

## 2.9 类型转换

Go 有着非常严格的强类型特征。Go 没有自动类型提升或类型转换。我们通过一个例子说明这意味着什么。

```go
package main

import (  
    "fmt"
)

func main() {  
    i := 55      //int
    j := 67.8    //float64
    sum := i + j //不允许 int + float64
    fmt.Println(sum)
}
```

```go
package main

import (  
    "fmt"
)

func main() {  
    i := 55      //int
    j := 67.8    //float64
    sum := i + int(j) //j is converted to int
    fmt.Println(sum)
}
```

```go
package main

import (  
    "fmt"
)

func main() {  
    i := 10
    var j float64 = float64(i) // 若没有显式转换，该语句会报错
    fmt.Println("j", j)
}
```

