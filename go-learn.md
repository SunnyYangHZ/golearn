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

# 3.常量

## 3.1 定义

在go语言语法中，常量表示固定的值。如：6,7,5.6，"hello world"，等。

```go
var a int=5
var b string="hello world"
```

在上述代码中，变量a，b分别被赋值常量5，“hello world”。关键字const被用于表示常量。

```go
package mian
func main(){
    const a=5
    a=89 //不能重新赋值
}
```

同时不能将函数的返回值赋值给常量。

```go
package main
import(
	"fmt"
	"math"
)
func main(){
    fmt.Println("hello world")
    var a=math.Sqrt(4)//可以
    const b=math.Sqrt(4)//不可以
}
```

## 3.2 字符串常量

双引号中的任何值都是 Go 中的字符串常量。例如像 `Hello World` 或 `Sam` 等字符串在 Go 中都是常量。什么类型的字符串属于常量？答案是他们是无类型的。像hello world 这样的字符串常量没有任何类型。

```go
const hello="hello world"
```

上述的hello常量没有类型。

在go语言中，所有的变量必须有明确的类型。如何将无类型的常量赋值给变量呢。

```go
package main
import(
	"fmt"
)
func main(){
    var name="sam"
    fmt.Printf("type %T value %v",name,name)
}

```

表明无类型的常量有一个与他们相关联的默认类型，并且当且仅当一行代码需要时才提供他，在声明中 var name="sam",name需要一个类型，它从字符串常量sam的默认类型中获取。

可以通过以下方式创建一个有类型常量。

```go
const typedhello string="hello world"
```

上述代码中，typedhello就是一个string类型的常量。

同时，go语言规定，在分配过程中混合类型是不允许的。

```go
package main
func main(){
var defaultName="sam"//允许
type mystring string
var customName mystring="sam"//允许
customName=defaultName//不允许
}
```

在上述代码中，我们首先创建一个变量defaultName并分配一个常量sam，常量sam的默认类型是string，所以在赋值后defaultName的类型是string。

之后，我们创建了一个新类型mystring，底层是string。同时我们创建了一个mystring的变量customName，并赋值sam，此时customName的类型是mystring。

现在我们我们将defaultName赋值给customName是不被允许的。

## 3.3 布尔常量

布尔常量和字符串常量没有什么不同。他们是两个无类型的常量 `true` 和 `false`。字符串常量的规则适用于布尔常量，所以在这里我们不再重复。以下是解释布尔常量的简单程序。

```go
package main

func main() {  
    const trueConst = true
    type myBool bool
    var defaultBool = trueConst // 允许
    var customBool myBool = trueConst // 允许
    defaultBool = customBool // 不允许
}
```

## 3.4 数字常量

数字常量包含整数、浮点数和复数的常量。

```go
package main

import (  
    "fmt"
)

func main() {  
    const a = 5
    var intVar int = a
    var int32Var int32 = a
    var float64Var float64 = a
    var complex64Var complex64 = a
    fmt.Println("intVar",intVar, "\nint32Var", int32Var, "\nfloat64Var", float64Var, "\ncomplex64Var",complex64Var)
}
```

上面的程序，常量 `a` 是没有类型的，它的值是 `5` 。您可能想知道 `a` 的默认类型是什么，如果它确实有一个的话, 那么我们如何将它分配给不同类型的变量。答案在于 `a` 的语法。下面的程序将使事情更加清晰。

```go
package main

import (  
    "fmt"
)

func main() {  
    var i = 5
    var f = 5.6
    var c = 5 + 6i
    fmt.Printf("i's type %T, f's type %T, c's type %T", i, f, c)

}
```

在上面的程序中，每个变量的类型由数字常量的语法决定。`5` 在语法中是整数， `5.6` 是浮点数，`5+6i` 的语法是复数。当我们运行上面的程序，它会打印出 `i's type int, f's type float64, c's type complex128`。

```go
package main

import (  
    "fmt"
)

func main() {  
    const a = 5
    var intVar int = a
    var int32Var int32 = a
    var float64Var float64 = a
    var complex64Var complex64 = a
    fmt.Println("intVar",intVar, "\nint32Var", int32Var, "\nfloat64Var", float64Var, "\ncomplex64Var",complex64Var)
}
```

在这个程序中， `a` 的值是 `5` ，`a` 的语法是通用的（它可以代表一个浮点数、整数甚至是一个没有虚部的复数），因此可以将其分配给任何兼容的类型。这些常量的默认类型可以被认为是根据上下文在运行中生成的。 `var intVar int = a` 要求 `a` 是 `int`，所以它变成一个 `int` 常量。 `var complex64Var complex64 = a` 要求 `a` 是 `complex64`，因此它变成一个复数类型。很简单的:)。

## 3.5 数字表达式

数字常量可以在表达式中自由混合和匹配，只有当它们被分配给变量或者在需要类型的代码中的任何地方使用时，才需要类型。

```go
package main

import (  
    "fmt"
)

func main() {  
    var a = 5.9/8
    fmt.Printf("a's type %T value %v",a, a)
}
```

在上面的程序中， `5.9` 在语法中是浮点型，`8` 是整型，`5.9/8` 是允许的，因为两个都是数字常量。除法的结果是 `0.7375` 是一个浮点型，所以 `a` 的类型是浮点型。这个程序的输出结果是: `a's type float64 value 0.7375`。

# 4.函数

## 4.1 函数声明

函数声明以关键字func开始，后面紧跟自定义的函数名functionname（函数名），函数的参数列表定义在（）里，返回值的类型则定义在之后的returntype（返回值类型）中，声明一个参数的语法采用**参数名 参数类型**的形式，任意多个参数采用类似（参数1 参数1的类型，参数2 参数2的类型）的形式指定。之后再{}之中的就是函数体。

语法如下：

```go
func functionname(parametername type)returntype{
    //函数体（具体实现的功能）
}
```

## 4.2 示例函数

下面我们将举例说明：

```go
func calculateBill(price int,no int)int{
    var totalPrice=price*no //商品总价=商品单价*数量
    return totalPrice //返回总价
}
```

例中函数有两个整型的输入price和no，返回值totalPrice为price和no的乘积，也是整数类型。

如果有连续若干个参数，他们的类型一致，我们无需一一罗列，只需在最后一个参数后添加该类型。如：**price int，no int**可以简写为**price，no int**，即上诉函数可以写作：

```go
func calculateBill(price,no int)int{
    var totalPrice=price*no
    return totalPrice
}
```

## 4.3函数调用

如上函数的调用方式：

```go
calculateBill(5,6)
```

完整程序如下：

```go
package main
import "fmt"
func calculateBill(price,no int)int{
    var totalPrice=price*no
    return totalPrice
}
func main{
    price,no:=5,6
    totalPrice:=calculateBill(price,no)
    fmt.Println("Total price is",totalPrice)
}
```

## 4.4 多返回值

go语言支持程序有多个返回值。

例：

```go
package main
import "fmt"
func rectProps(length,width float64)(float64,float64){
    var area=length*width
    var permeter=(length+width)*2
    return area,perimeter
}
func main(){
    area,perimeter:=rectProps(2.5,3.6)
    fmt.Printf("area %f perimeter %f",area,perimeter)
}
```

## 4.5 命名返回值

从函数中可以返回一个命名值，当命名了返回值，可以认为这些值在函数第一行就被声明为变量了。

```go
func rectProps(length,width float64)(area,periieter float64){
    area=length*width
    permeter=(length+width)*2
    return   //不需要明确指定返回值，默认返回area，permeter的值
}
```

## 4.6 空白符

_在go中被用作空白符，可以用作表示任何类型的任何值。

我们继续以rectProps函数为例，该函数计算的是面积和周长。假如我们只需要计算面积，而并不关心周长的计算结果。此时，就要用到空白符**_**。

即：

```go
package main
import "fmt"
func rectProps(length,width float64)(float64,float64){
    var area=length*width
    var perimeter=(length+width)*2
    return area,perimeter
}
func main(){
    area,_:=rectProps(5.6,7.8)
    fmt.Printf("Area %f",area)
}
```

# 5.包

## 5.1 什么是包，为什么使用包

我们所看到的go程序都只有一个文件，文件里包含一个main函数和其他函数，但在实际开发中，这种把所有的源代码都放到一个文件的方式并不好，这种编写方式，代码的重用和维护都会非常困难。而包package解决了这个问题。

包用于组织go源码，提供了更好的可重用性欲可读性。由于包提供了代码的封装，因此go应用程序更易维护。

## 5.2 main函数与main包

所有课执行的go程序都必须包含一个main函数，这个函数的程序运行的入口，main函数应该房子啊main包中。

***package packagename*这行代码指定了某一源文件属于一个包，它应该放在每一个源文件的第一行**，下面开始为程序创建一个main函数和main包。**在go工作区内的src文件夹中创建一个文件夹，命名为geometry**。在geometry文件夹中创建一个geometry.go文件。

代码如下：

```go
package main
import "fmt"
func main(){
    fmt.Println("geometrical shape properties")
}
```

*package main*这一行指定该文件属于main包，import “packagename”语句用于导入一个已存在的包，这里我们导入了*fmt*包，包内包含Println方法。之后是main函数，他会打印输出语句。

键入*go install geometry*，编译上述程序。该命令会在geometry文件夹内搜索拥有main函数的文件。在这里，它找到了geometry.go。接下来，它编译并产生一个名为geometry（在Windows下是geometry.exe）的二进制文件，该二进制文件放置于工作区的bin文件夹，现在，工作区的目录结构会是这样

```
src
	geometry
	geometry.go
bin
	geometry
```

键入workspacepath/bin/geometry，运行该程序。用自己的工作区来替换workspacepath，这个命令会执行bin文件夹里的geometry二进制文件。

## 5.3 创建自定义的包

我们将组织代码，使得所有与矩形有关的功能都放入rectangle包中，我们会创建一个自定义包rectangle，它有一个计算矩形面积和对角线的函数。

**属于某一个包的源文件都应该放置于一个单独命名的文件夹里。按照go的惯例，应该用包名命名该文件夹。**

因此我们在gemetry文件夹中，创建一个命名为rectangle的文件夹，在rectangle文件夹中，所有的文件都会以package rectangle作为开头，因为他们都属于rectangle包。

在我们创建的rectangle文件夹中，再创建一个名为rectprops.go的文件，编辑代码。

```go
//rectprops.go
package rectangle
import "math"

func Area(len,wid float64)float64{
    area:=len*wid
    return area
}
func Diagonal(len,wid float64)float64{
    diagonal:=math.Sqrt((len*len)+(wid*wid))
    return diagonal
}

```

在上述代码中，我们创建了两个函数用于计算Area和Diagonal。矩形的面积是长、宽乘积。矩形的对角线是长、宽平方和的平方根，math包下的Sqrt函数用于计算平方根。

这里函数Area和Diagonal都是以**大写字母开头**，之后解释原因。

## 5.4 导入自定义包

为了使用自定义包，我们必须要先导入它，导入自定义包的语法为import path。这里我们必须制定自定义包相对于工作区src文件夹的相对路径，此时的文件结构是：

```go
src
	geometry
		geometry.go   //包含main函数和main包
		rectangle
			rectprops.go
```

则在geometry.go里加入如下代码：

```go
//geometry.go
package main

import(
	"fmt"
	"geometry/rectangle"//导入自定义包
)
func main(){
    var rectlen,rectWide float64=5,6
    fmt.Println("geometrical shape properties")
    fmt.Printf("area of rectangle %.2f\n",rectangle.Area(rectLen,rectWide))
    fmt.Printf("diagonal of the rectangle %.2f",rectangle.Diagonal(rectLen,rectWide))
}
```

上述代码导入了rectangle包，并调用了里面的Area和Diagonal函数，得到矩形的面积和对角线。Printf内的格式说明符%.2f会将浮点数截断到小数点两位。

## 5.5 导出名字

我们在上述留下一个疑问，为什么Area和Diagonal首字母要大写，在go语言中，任何以大写字母开头的变量或者函数都是被导出的名字，其他包只能访问被导出的函数和变量。这里，我们需要在main包中访问Area和Diagonal函数，因此会将他们的首字母大写。

在rectprops.go中，如果函数名从Area(len,wid float64)变为area(len,wid float64),并且在geometry.go中，rectangle.Area(rectlen,rectWide)变为rectangle.area(rectlen,rectWide)则在程序运行过程中会抛出错误。

## 5.6 init函数

所有包都可以包含一个init函数，init函数不应该有任何返回值类型和参数。在我们的代码中也不能显式地调用。init函数形式如下：

```go
func init(){
    
}
```

init函数可用于执行初始化任务，也可用于在开始执行之前验证程序的正确性。

包的初始化顺序如下：

1. 首先初始化包级别（package level）的变量
2. 紧接着调用init函数，包可以有多个init函数（在一个或多个文件中），他们按照编译器解析他们的顺序进行调用。

如果一个包导入了另一个包，会先初始化被导入的包，尽管一个包可能会被导入多次，但只初始化一次。为了理解init函数，我们接下来对程序做了一些修改。

首先在rectprops.go文件中添加了一个init函数。

```go
//rectprops.go
package rectangle


import(
	"math"
	"fmt"
)
func init(){
    fmt.Println("rectangle package initialized")
    
}
func Area(len,wid float64)float64{
    area:=len*wid
    return area
}

func Diagonal(len,wid float64)float64{
    diagonal:=math.Sqrt((len*len)+(wid*wid))
    return diagonal
}
```

我们仅仅添加了init函数，并实现打印功能。

之后，我们来修改main包。我们知道矩形的长和宽都大于0，我们将在geometry.go中使用init函数和保级别变量来检查矩形的长和宽。

修改gemetry.go

```go
//gemetry.go
package main
import(
	"fmt"
	"geometry/rectangle"//导入自定义包
	)
var rectLen,rectWidth float64=5,6 //包级别变量
func init(){
    //init函数检查长宽是否大于0
    fmt.Println("main package initialized")
    if rectLen<0{
        log.Fatal("length is less than zero")
    }
    if rectWidth<0{
        log.Fatal("width is less than zero")
    }
}

func main(){
    fmt.Println("Geometrical shape properties")
    fmt.Printf("area of rectangle %.2f\n",rectangle.Area(rectLen,rectWidth))
fmt.Printf("diagonal of the rectangle %.2f ",rectangle.Diagonal(rectLen, rectWidth))
}
```

我们对geometry.go 做了如下修改：

	1. 变量rectLen和rectWidth从main函数级别转移到了包级别。
 	2. 添加了init函数。当rectLen或rectWidth小于0时，init函数使用log.Fatal函数打印一条日志，并终止程序。

main包的初始化顺序为：

	1. 首先初始化被导入的包，因此，首先初始化了rectangle包。
 	2. 接着初始化了包级别的变量rectLen和rectWidth。
 	3. 调用init函数。
 	4. 最后调用main函数。

运行结果：

```
rectangle package initialized  
main package initialized  
Geometrical shape properties  
area of rectangle 42.00  
diagonal of the rectangle 9.22
```

## 5.7 使用空白标识符

导入了包，却不使用它，这在go语法中是违法的，为避免报错可以使用空白标识符。

如下代码可以避免错误发生

```go
package main

import (  
    "geometry/rectangle" 
)

var _ = rectangle.Area // 错误屏蔽器

func main() {

}
```

`var _ = rectangle.Area` 这一行屏蔽了错误。我们应该了解这些错误屏蔽器（Error Silencer）的动态，在程序开发结束时就移除它们，包括那些还没有使用过的包。由此建议在 import 语句下面的包级别范围中写上错误屏蔽器。

有时候我们导入一个包，只是为了确保它进行了初始化，而无需使用包中的任何函数或变量。例如，我们或许需要确保调用了 rectangle 包的 init 函数，而不需要在代码中使用它。这种情况也可以使用空白标识符，如下所示。

```go
package main 

import (
    _ "geometry/rectangle" 
)
func main() {

}
```

运行上面的程序，会输出 `rectangle package initialized`。尽管在所有代码里，我们都没有使用这个包，但还是成功初始化了它。



