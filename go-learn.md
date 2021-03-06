

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



# 6.if-else语句

if是条件语句，语法结构是：

```go
if condition{
    
}
```

如果condition为真，则执行{ }之间的代码。

if语句还有可选部分即else if和else。

```go
if condition{
    //其他语句
}else if condition{
    //语句
}else{
    
}
```

if-else语句之间可以有任意数量的else if，条件判断顺序是从上到下，如果if或者else if条件判断为真，则执行相应的代码块。如果没有条件为真，则else代码块被执行。

例：检测数字的奇偶性

```go
package main
import "fmt"
func main(){
    num:=10
    if num%2==0{
        fmt.Println("the nember is even")
    }else{
        fmt.Println("the num is odd")
    }
}
```

如果 num%2==0语句检测到num取2的余数为0，则但因输出“the number is even”，否则输出“the number is odd”

if还有另外一种形式，包含一个statement可选语句部分，该组件在条件判断之前运行。语法为：

```go
if statement;condition{
    
}
```

重写上述判断奇偶代码：

```go
package main
import "fmt"
func main(){
    if num:=10;num%2==0{
        fmt.Println(num,"is even")
    }else{
        fmt.Println(num,"is odd")
    }
}
```

在上面的程序中，num在if语句中进行初始化，num只能从if和else中访问，也就是说num的范围仅限于if-else代码块，如果我们试图从if-else外部访问num，则不能编译通过。

让我们再写一个使用 `else if` 的程序。

```go
package main

import (  
    "fmt"
)

func main() {  
    num := 99
    if num <= 50 {
        fmt.Println("number is less than or equal to 50")
    } else if num >= 51 && num <= 100 {
        fmt.Println("number is between 51 and 100")
    } else {
        fmt.Println("number is greater than 100")
    }

}
```

在上面的程序中，如果 `else if num >= 51 && num <= 100` 为真，程序将输出 `number is between 51 and 100`。



**注意**

`else` 语句应该在 `if` 语句的大括号 `}` 之后的同一行中。如果不是，编译器会不通过。

让我们通过以下程序来理解它。

```go
package main

import (  
    "fmt"
)

func main() {  
    num := 10
    if num % 2 == 0 { //checks if number is even
        fmt.Println("the number is even") 
    }  
    else {
        fmt.Println("the number is odd")
    }
}
```

在上面的程序中，`else` 语句不是从 `if` 语句结束后的 `}` 同一行开始。而是从下一行开始。这是不允许的。如果运行这个程序，编译器会输出错误，

在 Go 语言规则中，它指定在 `}` 之后插入一个分号，如果这是该行的最终标记。因此，在if语句后面的 `}` 会自动插入一个分号。

实际上我们的程序变成了

```go
if num%2 == 0 {  
      fmt.Println("the number is even") 
};  //semicolon inserted by Go
else {  
      fmt.Println("the number is odd")
}
```

分号插入之后。从上面代码片段可以看出第三行插入了分号。

由于 `if{…} else {…}` 是一个单独的语句，它的中间不应该出现分号。因此，需要将 `else` 语句放置在 `}` 之后处于同一行中。

我已经重写了程序，将 else 语句移动到 if 语句结束后 `}` 的后面，以防止分号的自动插入。

```go
package main

import (  
    "fmt"
)

func main() {  
    num := 10
    if num%2 == 0 { //checks if number is even
        fmt.Println("the number is even") 
    } else {
        fmt.Println("the number is odd")
    }
}
```

# 7.循环

for是go语言中唯一存在的循环语句。

## 7.1 for循环语句语法

```go
for initialisation;condition;post{
    
}
```

初始化语句只执行一次，循环初始化后，将检查循环条件，如果条件的计算结果为true，则{}内的循环将被执行，接着执行post语句，post语句将在每次成功循环迭代后执行。在执行post语句后，条件将被再次检查，如果为true，则循环继续被执行，否则结束循环。

例：

```go
package main
import "fmt"
func main(){
    for i:=1;i<=10;i++{
        fmt.Printf("%d",i)
    }
}
```

## 7.2 break

break语句用于在完成正常执行之前突然中止for循环，之后程序将会在for循环下一行代码开始执行。

如；

```go
package main
import "fmt"
func main(){
    for i:=1;i<=10;i++{
        if i>5{
            break
        }
        fmt.Printf("%d",i)
    }
    fmt.Printf("\nline after for loop")
}
```

在上述程序中，循环过程i的值会被判断，如果i的值大于5，之后break语句会执行，循环就会被中止，打印语句会在for循环结束后执行。输出结果为：

```
1 2 3 4 5  
line after for loop
```

## 7.3 continue

continue语句用来跳出for循环中当前循环，在continue语句后的所有for循环语句都不会再本次循环中执行。循环体会在下一次循环中继续执行。

接下来我们写一个打印1到10并且使用continue的程序

```go
package main
import "fmt"
func main(){
    for i:=1;i<=10;i++{
        if i%2==0{
            continue
        }
        fmt.Printf("%d",i)
    }
}
```

在上述程序中，代码 *if i%2==0*会判断i除以2的余数是不是0，如果是0，这个数字就是偶数，然后执行continue语句，从而控制程序进入下一个循环体，因此在continue后面的打印语句不会被执行而进入下一个循环。输出1 3 5 7 9.

## 7.4 更多例子

下面程序打印从0到10所有的偶数。

```go
package main
import "fmt"
func main(){
    i:=0
    for ;i<=10;{
        fmt.Printf("%d",i)
        i+=2
    }
}
```

正如我们已经知道的，for循环包含三个部分，初始化语句，条件语句，post语句。这三个语句都是可选的，在上述程序中，初始化语句和post语句都被省略了。i在for循环外被初始化为0，只要i<=10循环就被执行。在循环外，i以2的增量自增。输出0 2 4 6 8 10.

上述程序也可被重写为：

```go
package main

import (  
    "fmt"
)

func main() {  
    i := 0
    for i <= 10 { //semicolons are ommitted and only condition is present
        fmt.Printf("%d ", i)
        i += 2
    }
}
```

在for循环中可以声明和操作多个变量，让我们来使用声明多个变量来打印如下程序

```
10 * 1 = 10  
11 * 2 = 22  
12 * 3 = 36  
13 * 4 = 52  
14 * 5 = 70  
15 * 6 = 90  
16 * 7 = 112  
17 * 8 = 136  
18 * 9 = 162  
19 * 10 = 190
```

```go
package main
import "fmt"
func main(){
    for no,i:=10,1;i<=10&&no<=19;i,no=i+1,no+1{
        fmt.Printf("%d*%d=%d\n",no,i,no*i)
    }
}
```

在上面程序中no和i被声明然后分别被初始化为10和1，在每一次循环结束后no和i都自增1.布尔操作符&&被用来确保i小于等于10并且no小于等于19.

## 7.5 无限循环

语法：

```go
for{
    
}
```

以下程序为一直打印hello world

```go
package main
import "fmt"
func main(){
    for{
        fmt.Println("hello world")
    }
}
```

# 8.switch语句

switch是一个条件语句，用于将表达式的值与可能匹配的选项列表进行比较，并根据匹配情况执行相应的代码块，它可以被认为是替代多个if-else子句的常用方式。

示例如代码所示：

```go
package main
import "fmt"
func main(){
    figer:=4
    switch finger{
        case 1:
        fmt.Println("Thumb")
        case 2:
        fmt.Println("Index")
        case 3:
        fmt.Println("Middle")
        case 4:
        fmt.Println("Ring")
        case 5:
        fmt.Println("Pinky")
    }
}
```

在上述程序中，switch finger将finger的值与每个case语句进行比较。通过从上到下对每一个值进行对比，并执行与选项值匹配的第一个逻辑。在上述代码中，finger的值为4，因此打印的结果是Ring。在选项列表中，case不允许出现重复项。如果存在重复，则会抛出错误。

```go
package main
import "fmt"
func main(){
    finger:=4
    switch finger{
        case 1:
        fmt.Println("Thumb")
        case 2:
        fmt.Println("Index")
        case 3:
        fmt.Println("Middle")
        case 4:
        fmt.Println("Ring")
        case 4:
        fmt.Println("Another Ring")
        case 5:
        fmt.Println("Pinky")
       
    }
}
```

## 8.1 默认情况

当存在与其他所有情况都不匹配时，将执行默认情况。

```go
package main
import "fmt"
func main(){
    switch finger:=8;finger{
        case 1:
        fmt.Println("Thumb")
        case 2:
        fmt.Println("Index")
        case 3:
        fmt.Println("Middle")
    case 4:
        fmt.Println("Ring")
    case 5:
        fmt.Println("Pinky")
        default:
        fmt.Println("incorrect finger number")
    }
}
```

在上述程序中，finger的值是8，它不符合其中任何一种情况，因此会打印 incorrect finger number。default不一定只能出现在switch语句的最后，他可以放在switch语句的任何地方。

在上述代码中，变量的声明方式被改变了，作用范围只局限于这个switch。

## 8.2 多表达式判断

通过用逗号分隔，可以在一个case中包含多个表达式。

```go
package main
import "fmt"
func main(){
    letter:="i"
    switch letter{
        case "a","e","i","o","u":
        fmt.Println("vowel")
        default:
        fmt.Println("not a vowel")
    }
}
```

在 `case "a","e","i","o","u":` 这一行中，列举了所有的元音。只要匹配该项，则将输出 `vowel`。

## 8.3 无表达式的switch

在switch语句中，表达式是可选的，可以被省略。如果省略了表达式，则表示这个switch语句等同于switch true，并且每个case表达式都被认定为有效，相应的代码块也会被执行。

```go
package main
import "fmt"
func main(){
    num:=75
    switch{
        case num>=0&&num<=50:
        fmt.Println("num is greater than 0 and less than 50")
        case num>=51&&num<=100:
        fmt.Println("num is greater than 51 and less than 100")
        case num>=101:
        fmt.Println("num is greater than 100")
    }
}
```

在上述代码中，switch中缺少表达式，因此默认它为true，true值会和每一个case的值结果进行匹配，case num>=51&&<=100：为true，所以输出num is greater than 51 and less than 100。这种类型的switch语句可以替代多个if-else子句。

## 8.4 Fallthrough语句

在go中，每执行完一个case后，会从switch语句中跳出来，不在做后续case的判断和执行。使用`fallthrough`语句可以在已经执行完成的case之后，把控制权转移到下一个case的执行代码中。

代码示例如下：

```go
package main
import "fmt"
func number()int{
    num:=15*5
    return num
}

func main(){
    switch num:=number();{
        case num<50:
        fmt.Printf("%d is lesser than 50\n",num)
        fallthrough
        case num<100:
        fmt.Printf("%d is lesser than 100\n",num)
        fallthrough
        case num<200:
        fmt.Printf("%d is lesser than 200",num)
    }
}
```

switch和case的表达式不一定是常量，他们也可以在运行过程中通过计算得到，在上述程序中，num被初始化为函数number（）的返回值，程序运行到switch中时，会计算出case的值，case num<100:的结果为true，所以程序输出 `75 is lesser than 100`.当执行到下一句fallthrough时，程序控制直接跳转到下一个case的第一个执行逻辑中，所以打印出`75 is lesser than 200`.最后这个程序的输出是：

```
75 is lesser than 100  
75 is lesser than 200
```

**`fallthrough` 语句应该是 case 子句的最后一个语句。如果它出现在了 case 语句的中间，编译器将会报错：`fallthrough statement out of place`**

# 9.数组和切片

## 9.1 数组

数组是同一类型的集合，例如：整数集合5,6,7,8形成一个数组。go语言中不允许混合不同类型的元素。例如包含字符串的整数的数组。

### 9.1.1 数组的声明

一个数组的表示形式为[n]T。n表示数组中元素的数量，T表示每个元素的类型。元素的数量n也是该类型的一部分。

可以使用不同的方式来声明数组：

```go
package main
import "fmt"
func main(){
    var a[3]int
    fmt.Println(a)
}
```

var a[3]int声明了一个长度为3的整型数组。**数组中的所有元素都被自动赋值为数组类型的零值。在这种情况下，a是一个整型数组，因此a的所有元素都被赋值为0，即int型的零值。输出结果为[0 0 0].

数组的索引从0开始到length-1结束，下面我们将为上述数组赋值。

```go
package mian
import "fmt"
func main(){
    var a[3]int
    a[0]=10
    a[1]=9
    a[2]=8
    fmt.Println(a)
}
```

输出结果为[10 9 8]

### 9.1.2 简略声明

下面我们用简略声明来创建相同的数组

```go
package main
import "fmt"
func main(){
    a:=[3]int{10,9,8}
    fmt.Println(a)
	}
```

输出结果为：[10 9 8]

在简略声明中，我们也不需要将数组中所有元素赋值：

```go
package main
import "fmt"
func main(){
    a:=[3]int{12}
    fmt.Println(a)
}
```

上述程序声明了一个长度为3的数组，但只提供了一个数值12，其他自动赋值0，输出结果为：[12 0 0]

在声明过程中，我们也可以不去声明长度，用`...`代替，编译器自动计算长度：

```go
package main
import "fmt"
func main(){
    a:=[...]int{10,9,8}
    fmt.Println(a)
}
```

**数组的大小是类型的一部分**，因此[12]int和[15]int是不同类型，数组不能调整大小。

```go
package main
func main(){
    a:=[3]int{5,6,7}
    var b [5]int
    b=a
}
```

运行此程序会抛出错误。

### 9.1.3 数组的值类型

go中的数组是值类型而不是引用类型。这意味着当数组赋值给一个新的变量时，该变量会得到一个原始数组的一个副本如果对新变量进行更改，则不会影响原始数组。

```go
package main
import "fmt"
func main(){
    a:=[...]string{"USA","China","India","Germany","France"}
    b:=a
    b[0]="Singapore"
    fmt.Println("a is",a)
    fmt.Println("b is ",b)
}
```

在上述程序的第7行，a的副本被赋给b，在8行中，b的第一个元素改为Singapore，这不会再原始数组a中反映出来，输出为：

```
a is [USA China India Germany France]  
b is [Singapore China India Germany France]
```

同样，当数组作为参数传递给函数时，他们按照值传递，而原始数组保持不变。

```go
package main
import "fmt"
func changeLocal(num [5]int){
    num[0]=55
    fmt.Println("inside function",num)
}
func main(){
    num:=[...]int{5,6,7,8,8}
    fmt.Println("before passing to function",num)
    changeLocal(num)
    fmt.Println("after passing to function",num)
}
```

输出结果：

```
before passing to function  [5 6 7 8 8]
inside function  [55 6 7 8 8]
after passing to function  [5 6 7 8 8]
```

### 9.1.4 数组的长度

通过将数组作为参数传递给len函数，可以得到数组的长度。

```go
package main

import "fmt"
func main(){
    a:=[...]float64{1.2,3.4,5.6,7.8,9.0}
    fmt.Println("length of a is",len(a))
}
```

### 9.1.5 使用range迭代数组

for循环可用于遍历数组中的元素

```go
package main
import "fmt"
func main(){
    a:=[...]float64{1.2,3.4,5.6,7.8,9.0}
    for i:=0;i<len(a);i++{
        fmt.Printf("%d th element of a is %.2f\n",i,a[i])
    }
}
```

上面的程序使用for循环比阿尼数组中的元素，从索引0到length of the array -1，输出结果为：

```
0 th element of a is 1.20
1 th element of a is 3.40 
2 th element of a is 5.60 
3 th element of a is 7.80
4 th element of a is 9.00
```

go提供了一种更好，更简洁的方法，通过使用for循环的range方法来遍历数组。range返回索引和该索引的值：

```go
package main

import "fmt"
func main(){
    a:=[...]float64{1.2,3.4,5.6,7.8}
    sun:=float64(0)
    for i,v:range a{
        fmt.Printf("%d the element of a is %.2f\n",i,v)
        sum+=v
    }
    fmt.Println("\nsum of all elements of a",sum)
}
```

上述程序中的for i,v:=range a 利用的for循环range方式，返回索引和该索引处的值，并计算数组的综合，输出为：

如果我们只需要值或者索引，可以用“_"空白标识符替换索引来执行。

```go
for _,v:=range a{
    
}
```

上述for循环忽略索引，取值。

### 9.1.6 多维数组

go语言可以创建多维数组

```go
package main
import "fmt"
func printarry(a [3][2]string){
    for _,v1:=range a{
        for _,v2:=range v1{
            fmt.Printf("%s",v2)
        }
        fmt.Printf("\n")
    }
}

func main(){
    a:=[3][2]string{
        {"lion","tiger"},
        {"cat","dog"},
        {"pigeon","peacock"},
    }
    printarry(a)
    var b [3][2]string
    b[0][0]="apple"
    b[0][1]="samsung"
    b[1][0]="microsoft"
    b[1][1]="google"
    b[2][0]="AT&T"
    b[2][1]="T-Mobile"
    fmt.Printf("\n")
    printarray(b)
```

在上述程序的第 17 行，用简略语法声明一个二维字符串数组 a 。20 行末尾的逗号是必需的。

另外一个二维数组 b 在 23 行声明，字符串通过每个索引一个一个添加。这是另一种初始化二维数组的方法。

输出：

```
lion tiger
cat dog
pigeon peacock

apple samsung
microsoft google
AT&T T-Mobile
```

这就是数组，尽管数组看上去似乎足够灵活，但是它们具有固定长度的限制，不可能增加数组的长度。这就要用到 **切片** 了。事实上，在 Go 中，切片比传统数组更常见。

## 9.2 切片

切片是由数组建立的一种方便、灵活且功能强大的包装。切片本身不拥有任何数据，他们只是对现有数组的引用。

### 9.2.1 创建一个切片

带有T类型元素的切片由[]T表示

```go
package main
import "fmt"
func main(){
    a:=[5]int{1,2,3,4,5}
    var b []int=a[1:4]
    fmt.Println(b)
}
```

使用语法a[start:end]创建一个从a数组索引start开始到end-1结束的切片，因此，在上述程序的第9行中，a[1:4]从索引1到3创建了a数组的一个切片表示。因此，切片b的值为[2,3,4,5]

另一种切片的创建方法：

```go
package main
import "fmt"
func main(){
    c:=[]int{6,7,8}
    fmt.Println(c)
}
```

在上述程序中，c:=[]int{6,7,8}创建了一个有三个整型元素的数组，并返回一个存储在c中的切片引用。

### 9.2.2 切片的修改

切片自己不拥有任何数据，它只是底层数组的一种表示，对切片所做的任何修改都会反映在底层数组中。

```go
package main
import "fmt"
func main(){
    darr:=[...]int{5,6,7,8,9,1,2,3,4}
    dslice:=darr[2:5]
    fmt.Println("array before",darr)
    for i:=range dslice{
        dslice[i]++
    }
    fmt.Println("array after",darr)
}
```

在上述程序的第 9 行，我们根据数组索引 2,3,4 创建一个切片 `dslice`。for 循环将这些索引中的值逐个递增。当我们使用 for 循环打印数组时，我们可以看到对切片的更改反映在数组中。该程序的输出是

```
array before [5 6 7 8 9 1 2 3 4 ]  
array after [5 6 8 9 10 2 2 3 4]
```

当多个切片公用相同的底层数组时，每个切片所做的更改将反映在数组中。

```go
package main
import "fmt"
func main(){
    numa:=[3]int{78,79,80}
    nums1:=numa[:]
    nums2:=numa[:]
    fmt.Println("array befor change 1",numa)
    nums1[0]=100
    fmt.Println("array after modification to slice nums1",numa)
    nums2[1]=101
    fmt.Println("array after modification to slice nums2",numa)
}
```

`numa [:]` 缺少开始和结束值。开始和结束的默认值分别为 `0` 和 `len (numa)`。两个切片 `nums1` 和 `nums2` 共享相同的数组。该程序的输出是

```
array before change 1 [78 79 80]  
array after modification to slice nums1 [100 79 80] 
array after modification to slice nums2 [100 101 80]
```

### 9.2.3 切片的长度和容量

切片的长度是切片中的元素数，切片的容量是从创建切片索引开始的底层数据中的元素数。

通过代码来理解：

```go
package main
import "fmt"
func main(){
    fruitarry:=[...]string{"apple","orange","grape","mango","water melon", "pine apple", "chikoo"}
    fruitslice:=fruitarry[1:3]
    fmt.Printf("length of slice %d capacity %d",len(fruitslice),cap(fruitslice))
   }
```

在上述程序中，fruitslice是从fruitarray的索引1,2创建的，因此fruitlice的长度为2，fruitarry的长度为7，fruiteslice是从fruitarray的索引1创建的，因此，fruitslice的容量是从fruitarray索引为1开始，也就是说从orange开始，该值为6，因此，fruitslice的容量为6，该程序输出切片的长度为2容量为6。

### 9.2.4 使用make创建一个切片

`func make([]T,len,cap)[]T`通过传递类型，长度和容量来创建切片，容量是可选参数，默认值为切片长度，make函数创建一个数组，并返回应用该数组的切片。

```go
package main
import "fmt"
func main(){
    i:=make([]int,5,5)
    fmt.Println(i)
}
```

使用make创建切片时默认情况下这些值为零，上述程序的输出为[0 0 0 0 0 ]

### 9.2.5 追加切片元素

正如我们知道数组的长度是固定的，它的长度不能增加。切片是动态的，使用append可以将新元素追加到切片上。append函数的定义是`func append(s[]T,x...T)[]T`

**x...T**在函数定义中表示该函数接受参数x的个数是可变的，这些类型的函数被称为**可变函数**

下面通过程序来解释：

```go
package main
import "fmt"
func main(){
    cars:=[]string{"Ferrari","Honda","Ford"}
    fmt.Println("cars:",cars,"has old length",len(cars),"and capacity",cap(cars))
    cars=append(cars,"Toyota")
    fmt.Println("cars:",cars,"has new length",len(cars),"and capacity",cap(cars))
}
```

在上述程序中，cars的容量最初是3，之后，我们给cars添加了一个新元素，并把`append(cars,"Toyota")`返回的切片赋值给cars，现在cars的容量翻了一番，变成了6，输出为：

```
cars: [Ferrari Honda Ford] has old length 3 and capacity 3  
cars: [Ferrari Honda Ford Toyota] has new length 4 and capacity 6
```

切片类型的零值为nil。一个nil切片的长度和容量为0。可以使用append函数将值追加到nil切片。

```go
package main
import "fmt"
func main(){
    var names []string
    if names==nil{
        fmt.Println("slice is nil going to append")
        names=append(names,"John","Sebastian","Vinay")
        fmt.Println("names contents:",names)
    }
}
```

在上面的程序`names`是nil，我们已经添加了3个字符串给`names`，该输出是：

```
slice is nil going to append  
names contents: [John Sebastian Vinay]
```

也可以使用`...`运算符将一个切片添加到另一个切片。你可以在**可变参数函数**教程中了解有关此运算符的更多信息。

```go
package main
import "fmt"
func main(){
    veggies:=[]string{"potatoes","tomatoes","brinjal"}
    fruits:=[]string{"oranage","apples"}
    food:=append(veggies,fruits...)
    fmt.Println("food:",food)
}
```

在上述程序中，food通过`append(veggies,fruits...)`创建，程序输出为：

```
food: [potatoes tomatoes brinjal oranges apples]
```

### 9.2.6 切片的函数传递

我们可以认为，切片在内部可由一个结构体类型表示，表现形式为：

```go
type slice struct{
    Length int
    Capacity int
    ZerothElement *byte
}
```

切片包含长度，容量和指向数组第零个元素的指针。当切片传递给函数时，即使他通过值传递，指针变量也将引用相同的底层数组。因此，当切片作为参数传递给函数时，函数内所做的更改也会在函数外可见。

```go
package main
import "fmt"

func subtactOne(numbers []int){
    for i:=range numbers{
        numbers[i]-=2
    }
}

func main(){
    nos:=[]int{8,7,6}
    fmt.Println("slice before function call",nos)
    subtactOne(nos)
    fmt.Println("slice after function call",nos)
}
```

上述程序中，调用函数将切片中的每个元素递减2，在函数调用后打印切片时，这些更改时可见的，上述程序的输出是：

```
array before function call [8 7 6]  
array after function call [6 5 4]
```

### 9.2.7 多维切片

类似于数组，切片可以有多个维度。

```go
package main
import "fmt"
func main(){
    pls:=[][]string{
        {"C","C++"},
        {"JavaScript"},
        {"Go","Rust"},
    }
    for _,v1:=range pls{
        for _,v2:=range v1{
            fmt.Printf("%s",v2)
        }
        fmt.Printf("\n")
    }
}
```

程序的输出：

```
C C++  
JavaScript  
Go Rust
```

### 9.2.8 内存优化

切片持有对底层数组的引用。只要切片在内存中，数组就不能被垃圾回收，在内存管理方面，这是需要注意的。让我们假设我们有一个非常大的数组，我们只想处理它的一小部分，然后，我们由这个数组常见一个切片。并开始处理切片。这里需要重点注意的是，在切片引用时数组仍然存在内存中。

一种解决方法是使用copy函数`func copy(dst,src[]T)int`来生成一个切片副本，这样我们可以使用新的切片，原始数组可以被垃圾回收。

```go
package main
import "fmt"
func countries()[]string{
    countries:=[]string{"USA","Singapore","Germany","India","Australia"}
    neededCountries:=countries[:len(countries)-2]
    countriesCpy:=make([]string,len(neededCountries))
    copy(countriesCpy,neededCountries)
    return countriesCpy
}
func main(){
    countriesNeeded:=countries()
    fmt.Println(countriesNeeded)
}
```

在上述程序中，`needeCountries:=countries[:len(countries)-2]`创建一个去掉尾部2个元素的切片`countries`,将 `neededCountries` 复制到 `countriesCpy` 同时在函数的下一行返回 countriesCpy。现在 `countries` 数组可以被垃圾回收, 因为 `neededCountries` 不再被引用。

# 10.可变参数函数

可变参数函数是一种参数个数可变的函数。

## 10.1 语法

如果函数最后一个参数被记做...T，这时函数可以接受任意个T类型参数作为最后一个参数。

**注意：**只有函数最后一个参数才允许可变。

### 例子说明

append函数可以将不同数量的参数传递。

```go
func append(slice []Type,elems ...Type)[]Type
```

上面是append函数的定义，在定义中elems是可变参数，这样append函数可以接受可变化的参数。

让我们创建一个我们自己的可变参数函数：

```go
package main
import "fmt"
func find(num int,nums ...int){
    fmt.Printf("type of nums is %T\n",nums)
    found:=false
    for i,v:=range nums{
        if v==num{
            fmt.Println(num,"found at index",i,"in",nums)
            found=true
        }
    }
    if !found{
        fmt.Println(num,"not found in",nums)
    }
    fmt.Printf("\n")
}
func main(){
    find(89,89,90,95)
    find(45,56,67,45,90,109)
    find(78,38,56,98)
    find(87)
}
```

在上面程序中，`func find(num int,nums ...int)`中的`nums`可接受任意数量的参数，在find函数中，参数nums相当于一个整型切片。

**可变参数函数的工作原理是把可变参数转换为一个新的切片。以上面程序`find`函数中的可变参数是89,90,95。find函数接受一个int类型的可变参数。因此这三个参数被编译器转换为一个int类型切片`int []int{89,90,95}`然后被传入find函数。

## 10.2 给可变参数函数传入切片

```go
package main
import "fmt"
func find(num int,nums ...int){
    fmt.Printf("type of nums is %T\n",nums)
    found:=false
    for i,v:=range nums{
        if v==num{
            fmt.Println(num,"found at index",i,"in",nums)
            found=true
        }
    }
    if !found{
        fmt.Println(num,"not found in",nums)
    }
    fmt.Printf("\n")
}
func main(){
    nums:=[]int{89,90,95}
    find(89,nums)
}
```

在这种情况下，会抛出错误，因为函数要求传递的是可变参数类型，并不是需要切片类型。

当然也有一种方法可以实现对可变参数类型传入切片类型，具体做法如下：

**有一个可以直接将切片传入可变参数函数的语法糖，即在切片后加...后缀，这样，切片将直接传入函数，不再创建新的切片。**

即：

```go
package main

import (
    "fmt"
)

func find(num int, nums ...int) {
    fmt.Printf("type of nums is %T\n", nums)
    found := false
    for i, v := range nums {
        if v == num {
            fmt.Println(num, "found at index", i, "in", nums)
            found = true
        }
    }
    if !found {
        fmt.Println(num, "not found in ", nums)
    }
    fmt.Printf("\n")
}
func main() {
    nums := []int{89, 90, 95}
    find(89, nums...)
}
```

## 10.3 不直观错误

例：

```go
package main
import "fmt"
func change(s ...string){
    s[0]="Go"
}
func main(){
    welcome:=[]string{"hello","world"}
    change(welcome...)
    fmt.Println(welcome)
}
```

你认为这段代码将输出什么呢？如果你认为它输出 `[Go world]` 。恭喜你！你已经理解了可变参数函数和切片。如果你猜错了，那也不要紧，让我来解释下为什么会有这样的输出。

在第 13 行，我们使用了语法糖 `...` 并且将切片作为可变参数传入 `change` 函数。

正如前面我们所讨论的，如果使用了 `...` ，`welcome` 切片本身会作为参数直接传入，不需要再创建一个新的切片。这样参数 `welcome` 将作为参数传入 `change` 函数

在 `change` 函数中，切片的第一个元素被替换成 `Go`，这样程序产生了下面的输出值

```
[Go world]
```

# 11.Maps

map是在go中将值（value）与键（key）关联的内置类型。通过相应的键可以以获取到值。

## 11.1 如何创建map

通过向make函数传入键和值得类型，可以创建map。`make(map[type of key]type of value)`是创建map的语法。

```go
personSalary:=make(map[string]int)
```

上述代码创建一个名为personSalary的map，其中键是string类型，而值是int类型。

map的零值是nil，如果你想添加元素到nil map中，会触发运行时panic，因此map必须使用make函数初始化。

```go
package main
import "fmt"

func main(){
    var personSalary map[string]int
    if personSalary==nil{
        fmt.Println("map is nil.Going to make one.")
        personSalary=make(map[string]int)
    }
}
```

上述程序中，personSalary是nil，因此需要使用make方法初始化，程序将输出`map is nil.Going to make one`。

## 11.2给map添加元素

给map添加新元素的语法和数组相同。下面的程序给personSalary map添加几个新元素。

```go
package main
import "fmt"
func main(){
    personSalary:=make(map[string]int)
    personSalary["steve"]=1200
    personSalary["jamie"]=15000
    personSalary["mike"]=9000
    fmt.Println("personSalary map contents:",personSalary)
}
```



同时，也可以在声明的时候初始化map。

```go
package main
import "fmt"
func main(){
    personSalary:=map[string]int{
        "steve":12000,
        "jamie":15000,
    }
    personSalary["mike"]=9000
    fmt.Println("personSalary map contents:",personSalary)
}
```

上述程序在声明的同时添加了两个元素，之后又添加了mike。

## 10.3 获取map中的元素

目前我们已经给map添加了几个元素，获取map元素的语法是map[key]。

```go
package main
import "fmt"
func main(){
    personSalary:=map[string]int{
        "steve":12000,
        "jamie":15000,
    }
    personSalary["mike"]=9000
    employee:="jamie"
    fmt.Println("Salary of",employee,"is",personSalary[employee])
}
```

上述程序中，获取并打印员工 jamie的薪资，程序输出`Salary of jamie is 15000`。

当要获取一个不存在的元素时，map会返回该元素类型的零值。在`personSalary`这个map里，如果我们获取一个不存在的元素，会返回int类型的零值0.

```go
package main
import "fmt"
func main(){
    personSalary:==map[string]int{
        "steve":12000,
        "jamie":15000,
    }
    personSalary["mike"]=9000
    employee:="jamie"
    fmt.Println("Salary of ",employee,"is",personSalary[employee])
    fmt.Println("Salary of joe is",personSalary["joe"])
}
```

程序输出为：

```
Salary of jamie is 15000
Salary of joe is 0
```

上面程序返回`joe`的薪资是0，`personSalary`中不包含`joe`的情况下我们不会获取到任何运行时错误。如果我们想知道map中到底是不是存在这个`key`,该怎么做

```go
value,ok:=map[key]
```

上述就是获取map中某个key是否存在的语法，如果ok是true，表示key存在，key对应的值就是value，反之表示key不存在。

```go
package main
import "fmt"
func main(){
    personSalary:=map[string]int{
        "steve":12000,
        "jamie":15000,
    }
    personSalary["mike"]=9000
    newEmp:="joe"
    value,ok:=personSalary[newEmp]
    if ok==true{
        fmt.Println("Salary of",newEmp,"is",value)
    }else{
        fmt.Println(newEmp,"not found")
    }
}
```

程序输出：

```
joe not found
```

遍历map中所有的元素需要用`for range`循环

```go
package main
import "fmt"
func main(){
    personSalary:=map[string]int{
        "steve":12000,
        "jamie":15000,
    }
    personSalary["mike"]=9000
    fmt.Println("All items of a map")
    for key,value:=range personSalary{
        fmt.Printf("personSalary[%s]=%d\n",key,value)
    }
}
```

程序输出：

```
All items of a map
personSalary[mike] = 9000
personSalary[steve] = 12000
personSalary[jamie] = 15000
```

**有一点很重要，当使用`for range`遍历map时，不保证每次执行程序获取的元素顺序相同。**

## 10.4 删除map中的元素

删除`map`中`key`的语法是`delete(map,key)`。此函数没有返回值。

```go
package main
import "fmt"
func main(){
    personSalary:=map[string]int{
        "steve":12000,
        "jamie":15000,
    }
    personSalary["mike"]=9000
    fmt.Println("map before deletion",personSalary)
    delete(personSalary,"steve")
    fmt.Println("map after deletion",personSalary)
}
```

上述程序输出：

```
map before deletion map[steve:12000 jamie:15000 mike:9000]
map after deletion map[mike:9000 jamie:15000]
```

## 10.5 获取map的长度

获取map的长度使用`len()`函数

```go
package main
import "fmt"
func main(){
    personSalary:=map[string]int{
        "steve":12000,
        "jamie":15000,
    }
    personSalary["mike"]=9000
    fmt.Println("length is",len(personSalary))
}
```

上述程序的输出是，`length is 3`

## 10.6 map是引用类型

和slice类似，map也是引用类型，当map被赋值为一个新变量时，他们指向同一个内部数据结构。因此改变其中一个变量，会影响到另一个变量。

```go
package main
import "fmt"
func main(){
    personSalary:=map[string]int{
        "steve":12000,
        "jamie":15000,
    }
    personSalary["mike"]=9000
    fmt.Println("Original person salary",personSalary)
    newPersonSalary:=personSalary
    newPersonSalary["mike"]=18000
    fmt.Println("Person salary changed",personSalary)
}
```

输出为：

```
Original person salary map[steve:12000 jamie:15000 mike:9000]
Person salary changed map[steve:12000 jamie:15000 mike:18000]
```

## 10.7 map的相等性

map之间不能用==来判断相等，==只能用来检查map是否为nil。

```go
package main
func main(){
    map1:=map[string]int{
        "one":1,
        "two":2,
    }
    map2:=map1
    if map1==map2{
        
    }
}
```

上面程序抛出编译错误 **invalid operation: map1 == map2 (map can only be compared to nil)**。

判断两个 map 是否相等的方法是遍历比较两个 map 中的每个元素。

# 12.字符串

## 12.1 什么是字符串

go语言中的字符串是一个字节切片，把内容放在双引号“”之间，我们可以创建一个字符串。让我们来看一个创建并打印字符串的简单示例。

```go
package main
import "fmt"
func main(){
    name:="Hello World"
    fmt.Println(name)
}
```

上述程序会输出Hello World

## 12.2 单独获取字符串的每一个字节

由于字符串是一个字节切片，所以我们可以获取字符串的每一个字节。

```go
package main
import "fmt"
func printBytes(s string){
    for i:=0;i<len(s);i++{
        fmt.Printf("%x",s[i])
    }
}
func main(){
    name:="Hello World"
    printBytes(name)
}
```

上述程序中，`len(s)`返回字符串中字节的数量，然后我们用了一个for循环以16进制的形式打印这些字节。`%x`格式限定符用于指定16进制编码。上面的程序输出是`48 65 6c 6c 6f 20 57 6f 72 6c 64`。这些打印出来的字符是“hello world”以Unicode UTF-8编码的结果。

修改上述程序，让它打印字符串的每一个字符。

```go
package main
import "fmt"
func printBytes(s string){
    for i:=0;i<len(s);i++{
        fmt.Printf("%x",s[i])
    }
}
func printChars(s string){
    for i:=0;i<len(s);i++{
        fmt.Printf("%c",s[i])
    }
}
func main(){
    name:="Hello World"
    printBytes(name)
    fmt.Printf("\n")
    printChars(name)
}
```

其中`%c`格式限定符用于打印字符串的字符，输出为：

```
48 65 6c 6c 6f 20 57 6f 72 6c 64  
H e l l o   W o r l d
```

## 12.3 rune

rune 是go语言的内建类型，它也是int32的别称，在go语言中，rune表示一个代码点。代码点无论占用多少个字节，都可以用一个rune来表示。让我们修改上述程序，用rune来打印字符。

```go
package main
import "fmt"
func printBytes(s string){
    for i:=0;i<len(s);i++{
        fmt.Printf("%x",s[i])
    }
}
func printChars(s string){
    runes:=[]rune(s)
    for i:=0;i<len(runes);i++{
        fmt.Printf("%c",runes[i])
    }
}
func main(){
    name:="Hello World"
    printBytes(name)
    fmt.Printf("\n")
    printChars(name)
    fmt.Printf("\n\n")
    name="Señor"
    printBytes(name)
    fmt.Printf("\n")
    printChars(name)
}
```

在上述代码中，字符串被转化为一个rune切片，然后我们循环打印字符，输出结果是：

```
48 65 6c 6c 6f 20 57 6f 72 6c 64  
H e l l o   W o r l d 

53 65 c3 b1 6f 72  
S e ñ o r
```

## 12.4 字符串的for range循环

上面的程序是一种遍历字符串的好方法，但是go给我们提供了一种更简单的方法来实现，使用for range循环。

```go
package main
import "fmt"

func printCharsAndBytes(s string){
    for index,rune:=range s{
        fmt.Printf("%c starts at byte %d\n",rune,index)
    }
}
func main(){
    name"Señor"
    printCharsAndBytes(name)
}
```

使用`for range`遍历了字符串，循环返回的是当前rune的字节位置，输出为：

```
S starts at byte 0  
e starts at byte 1  
ñ starts at byte 2
o starts at byte 4  
r starts at byte 5
```

## 12.5用字节切片构造字符串

```go
package main
import "fmt"
func main(){
    byteSlice:=[]byte{0x43, 0x61, 0x66, 0xC3, 0xA9}
    str:=string(byteSlice)
    fmt.Println(str)
}
```

在上面的程序中 `runeSlice` 包含字符串 `Señor`的 16 进制的 Unicode 代码点。这个程序将会输出`Señor`。

## 12.6 字符串的长度

[utf8 package](https://golang.org/pkg/unicode/utf8/#RuneCountInString) 包中的 `func RuneCountInString(s string) (n int)` 方法用来获取字符串的长度。这个方法传入一个字符串参数然后返回字符串中的 rune 的数量。

```go
package main
import (
	"fmt"
	"unicode/utf8"
	)
func length(s string){
    fmt.Printf("lenght of %s is %d\n",s,utf8.RuneCountInString(s))
}
func main(){
    word1"Señor"
    length(word1)
    word2:="Pets"
    length(word2)
}
```

输出结果为：

```
length of Señor is 5  
length of Pets is 4
```

## 12.7 字符串是不可变的

为了修改字符串，我们需要把其转化为一个rune切片，对这个切片进行更改，之后再转化为一个字符串。

```go
package main
import "fmt"
func mutate(s []rune)string{
    s[0]='a'
    return string(s)
}
func main(){
    h:="hello"
    fmt.Println(mutate([]rune(h)))
}
```

`utate` 函数接收一个 rune 切片参数，它将切片的第一个元素修改为 `'a'`，然后将 rune 切片转化为字符串，并返回该字符串。程序的第 13 行调用了该函数。我们把 `h` 转化为一个 rune 切片，并传递给了 `mutate`。这个程序输出 `aello`。

# 13.指针

指针是一种存储内存地址的变量。

## 13.1指针的声明

指针变量的类型为***T**，该指针指向一个**T**类型的变量。

```go
package main
import "fmt"
func main(){
    b:=255
    var a *int=&b
    fmt.Printf("Type of a is %T\n",a)
    fmt.Printf("address of b is",a)
}
```

**&**操作符用于获取变量的地址，上述程序中我们把**b**的地址赋值为***int**类型的**a**。我们称**a**指向了**b**。当我们打印**a**的值时，会打印**b**的地址。

```
Type of a is *int  
address of b is 0x1040a124
```

由于b可能在内存中所处的位置不同，我们会得到不同的地址。

## 13.2指针的零值

指针的零值是nil

```go
package main
import "fmt"
func main(){
    a:=25
    var b *int
    if b==nil{
        fmt.Println("b is",b)
        b=&a
        fmt.Println("b after initialization is",b)
    }
}
```

上述程序中，`b`初始化为`nil`,接着将**a**的地址赋值给b，则程序会输出：

```
b is <nil>  
b after initialisation is 0x1040a124
```

## 13.3 指针的解引用

指针的解引用可以获取指针所指向的变量的值。将`a`解引用的语法是`*a`

```go
package main
import "fmt"
func main(){
    b:=255
    a:=&b
    fmt.Println("address of b is",a)
    fmt.Println("value of b is",*a)
}
```

上述程序的结果是：

```
address of b is 0x1040a124  
value of b is 255
```

下面我们通过指针来修改b的值

```go
package main
import "fmt"
func main(){
    b:=255
    a:=&b
    fmt.Println("address of b is",a)
    fmt.Println("value of b is",*a)
    *a++
    fmt.Println("new value of b is",b)
}
```

我们把 `a` 指向的值加 1，由于 `a` 指向了 `b`，因此 `b` 的值也发生了同样的改变。于是 `b` 的值变为 256。程序会输出：

```
address of b is 0x1040a124  
value of b is 255  
new value of b is 256
```

## 13.4 向函数传递指针参数

```go
package main
import "fmt"
func change(val *int){
    *val=55
}
func main(){
    a:=58
    fmt.Println("value of a before function call is",a)
    b:=&a
    change(b)
    fmt.Println("value of a after function call is",a)
}
```

在上述程序中，我们向函数`change`传递了指针变量`b`,而`b`存储了`a`的地址。而在`change`函数中，通过解引用修改了a的值，则程序输出：

```
value of a before function call is 58  
value of a after function call is 55
```

## 13.5 不要向函数传递数组的指针，而应该是使用切片

假如我们想要在函数内修改一个数组，并希望调用函数的地方也能得到修改后的数组，一种解决方案是把一个指向数组的指针传递给这个函数。

```go
package main
import "fmt"
func modify(arr *[3]int){
    (*arr)[0]=90
   
}
func main(){
    a:=[3]int{89,90,91}
    modify(&a)
    fmt.Println(a)
}
```

在上述程序中，我们将数组的地址传递给了modify函数，通过将arr解引用，重新给它赋值。

**`a[x]` 是 `(\*a)[x]` 的简写形式，因此上面代码中的 `(\*arr)[0]` 可以替换为 `arr[0]`**。下面我们用简写形式重写以上代码。

```go
package main
import "fmt"
func modify(arr *[3]int){
    arr[0]=90
}
func main(){
    a:=[3]int{89,90,91}
    modify(&a)
    fmt.Println(a)
}
```

该程序也会输出[90 90 91]

**这种方式向函数传递一个数组指针参数，并在函数内修改数组。尽管它是有效的，但却不是go语言惯用的实现方式，我们最好使用切片来处理。

使用切片重写代码

```go
package main
import "fmt"
func modify(sls []int){
    sls[0]=90
}
func main(){
    a:=[3]int{89,90,91}
    modify(a[:])
    fmt.Println(a)
}
```

我们将一个切片传递给了 `modify` 函数。在 `modify` 函数中，我们把切片的第一个元素修改为 `90`。程序也会输出 `[90 90 91]`。**所以别再传递数组指针了，而是使用切片吧**。

## 13.6 go不支持指针运算

```go
package main

func main() {  
    b := [...]int{109, 110, 111}
    p := &b
    p++
}
```

上述程序会抛出错误。

# 14.结构体

## 14.1 什么是结构体

结构体是用户定义的类型，表示若干个字段（field）的集合。有时应该把数据整合在一起，而不是让这些数据没有联系。这种情况下可以使用结构体。

例：一个职员有`firstName`、`lastName`和`age`三个属性，而把这些属性组合在一起形成一个结构体employee中就很合理。

## 14.2 结构体的声明

```go
type Employee struct{
    firstName string
    lastName  string
    age       int
}
```

在上述代码中，声明了一个结构体类型`Employee`,它有`firstName`、`lastName`和`age`三个字段，通过把相同类型的字段声明在同一行，结构体可以变得更加紧凑，在上面的结构体中，`firstName`、和`lastName`属于相同的`string`类型，于是这个结构体可以重写为：

```go
type Employee struct{
    firstName,lastName string
    age,salary         int
}
```

上述的结构体称为命名的结构体。我们创建了名为Employee的新类型，而它可以用于创建`Employee`类型的结构体变量。

声明结构体时也可以不用声明一个新类型，这样的结构体类型称为**匿名结构体**

```go
var employee struct{
    firstName,lastName string
    age                int
}
```

上述代码片段创建了一个**匿名结构体**

## 14.3 创建命名的结构体

通过以下代码示例，我们去定义一个**命名的结构体**

```go
package main
import "fmt"

type Employee struct{
    firstName,lastName string
    age,salary         int
}
func main(){
    emp1:=Employee{
        firstName:"Sam",
        age      :25,
        salary   :500,
        lastName :"Anderson"
    }
    emp2:=Employee{"Thomas","Paul",29,800}
    fmt.Println("Employee 1",emp1)
    fmt.Println("Employee 2",emp2)
}
```

我们创建了一个命名的结构体 `Employee`。而在第 15 行，通过指定每个字段名的值，我们定义了结构体变量 `emp1`。字段名的顺序不一定要与声明结构体类型时的顺序相同。在这里，我们改变了 `lastName` 的位置，将其移到了末尾。这样做也不会有任何的问题。

在上面程序的第 23 行，定义 `emp2` 时我们省略了字段名。在这种情况下，就需要保证字段名的顺序与声明结构体时的顺序相同。

程序输出为：

```
Employee 1 {Sam Anderson 25 500}
Employee 2 {Thomas Paul 29 800}
```



## 14.4 创建匿名结构体

```go
package main
import "fmt"
func main(){
    emp3:=struct{
        firstName,lastName string
        age,salary         int
    }{
        firstName:"Andreah",
        lastName:"Nikola",
        age:    :31,
        salary  :5000,
    }
    fmt.Println("Employee 3",emp3)
}
```

在上述程序中，我们定义了一个**匿名结构体变量**`emp3`。这里只创建了一个新的结构体变量，而没有定义任何类型。

程序输出为：

```
Employee 3 {Andreah Nikola 31 5000}
```

## 14.5 结构体的零值

当定义好的结构体并没有被显式地初始化时，该结构体的字段将默认赋值为零。

```go
package main
import "fmt"
type Employee struct{
    firstName,lastName string
    age,salary         int
}
func main(){
    var emp4 Employee
    fmt.Println("Employee 4",emp4)
}
```

上述程序定义了`emp4`,却没有进行初始化，因此，`firstName`和`lastName`赋值为string的零值（“”）。而`age`和`salary`赋值为int的零值0，则程序的输出为：

```
Employee 4 { 0 0}
```

当然也存在一种情况，结构体中的某些字段被赋予了初始值，有些字段并没有赋予。这些忽略的字段则会被赋值为零。

```go
package main
import "fmt"
type Employee struct{
    firstName,lastName string
    age,salary         int
}
func main(){
    emp5:=Employee{
        firstName:"John",
        lastName:"Paul"
    }
    fmt.Println("Employee 5",emp5)
}
```

在上述程序中，我们初始化了`firstName`和`lastName`,而`age`和`salary`没有进行初始化。因此`age`和`salary`赋值为零值。该程序的输出：

```
Employee 5 {John Paul 0 0}
```

## 14.6 访问结构体的字段

点操作符`.`用于访问结构体的字段。

```go
package main
import "fmt"

type Employee struct{
    firstName,lastName string
    age,salary         int
}
func main(){
    emp6:=Employee{"Sam","Anderson",55,6000}
    fmt.Println("First Name:",emp6.firstName)
    fmt.Println("Last Name:",emp6.lastName)
    fmt.Println("Age:",emp6.age)
    fmt.Printf("Salary $%d",emp6.salary)
}
```

上述程序中**emp6.firstName**访问了结构体emp6的字段firstName，该程序的输出：

```
First Name: Sam  
Last Name: Anderson  
Age: 55  
Salary: $6000
```

还可以创建零值的`struct`,以后再给每个字段赋值。

```go
package main
import "fmt"

type Employee struct{
    firstName,lastName string
    age,salary         int
}
func main(){
    var emp7 Employee
    emp7.firstName="Jack"
    emp7.lastName="Adams"
    fmt.Println("Employee 7:",emp7)
}
```

在上述程序中，我们定义了`emp7`,接着给`firstName`和`lastName`赋值，则该程序输出：

```
Employee 7: {Jack Adams 0 0}
```

## 14.7 结构体的指针

我们也可以创建指向结构体的指针。

```go
package main
import "fmt"

type Employee struct{
    firstName,lastName string
    age,salary         int
}
func main(){
    emp8:=&Employee{"Sam","Anderson",55,6000}
    fmt.Println("First Name:",(*emp8).firstName)
    fmt.Println("Age:",(*emp8).age)
}
```

在上述程序中，emp8是一个指向结构体`Employee`的指针。`(*emp8).firstName`表示访问结构体`emp8`的`firstName`字段。输出为：

```
First Name: Sam
Age: 55
```

**go语言允许我们在访问firstName字段时，可以使用`emp8.firstName`来代替显式地解引用`(*emp8).firstName`

```go
package main
import "fmt"

type Employee struct{
    firstName,lastName string
    age,salary         int
}
func main(){
    emp8:=&Employee{"Sam","Anderson",55,6000}
    fmt.Println("First Name:",emp8.firstName)
    fmt.Println("Age:",emp8.age)
}
```

在上述程序中，我们使用`emp8.firstName`来访问`firstName`字段，输出：

```
First Name: Sam
Age: 55
```

## 14.8 匿名字段

当我们创建结构体时，字段可以只有类型，而没有字段名。这样的字段称为匿名字段

以下代码创建一个Person结构体，它含有两个匿名字段string和int。

```go
type Person struct{
    string
    int
}
```

利用匿名字段来编写一段程序。

```go
package main
import "fmt"
type Person struct{
    string
    int
}
func main(){
    p:=Person{"Naveen",50}
    fmt.Println(p)
}
```

在上述的程序中，结构体`Person`有两个匿名字段。p:=Person{"Naveen",50}定义了一个`Person`类型的变量。该程序输出`{Naveen 50}`。

**虽然匿名字段没有名称，但其实匿名字段的名称就默认为它的类型**。比如在上面的`Person`结构体里，虽说字段是匿名的，但go默认这些字段名是它们各自的类型。所以`Person`结构体有两个名为string和int的字段。

```go
package main
import "fmt"
type Person struct{
    string
    int
}
func main(){
    var p1 Person
    p1.string="naveen"
    p1.int=50
    fmt.Println(p1)
}
```

在上述程序中，我们访问了`Person`结构体的匿名字段，我们把字段类型作为字段名，分别为“string”和“int”，输出为：

```
{naveen 50}
```

## 14.9 嵌套结构体

结构体的字段也可能是另一个结构体，这样的结构体称为嵌套结构体。

```go
package main
import "fmt"

type Address struct{
    city,state string
}
type Person struct{
    name string
    age int
    address Address
}
func main(){
    var p Person
    p.name="Naveen"
    p.age=50
    p.address=Address{
        city:"Chicago",
        state:"Illinois"
    }
    fmt.Println("Name:"p.name)
    fmt.Println("Age:",p.age)
    fmt.Println("City:",p.address.city)
    fmt.Println("State:",p.address.state)
}
```

上述结构体`Person`有一个字段`address`,而`address`也是结构体，该程序输出：

```
Name: Naveen  
Age: 50  
City: Chicago  
State: Illinois
```

## 14.10 提升字段

如果是结构体中有匿名的结构体类型字段，该匿名结构体里的字段就称为提升字段。这是因为提升字段就像是属于外部结构体一样，可以用外部结构体直接访问。下面我们通过代码来理解。

```go
type Address struct{
    city,state string
}
type Person struct{
    name string
    age int
    Address
}
```

在上述代码中，Person结构体中有一个匿名字段Address，而Address是一个结构体，现在结构体Address有city和state两个字段，访问这两个字段就像在Person里直接声明的一样。我们称之为提升字段。

```go
package main
import "fmt"

type Address struct{
    city,state string
}
type Person struct{
    name string
    age  int
    Address
}

func main(){
    var p Person
    p.name="Naveen"
    p.age=50
    p.Address=Address{
        city:"Chicago",
        state:"Illinois"
    }
    fmt.Println("Name:",P.name)
    fmt.Println("Age:",p.age)
    fmt.Println("City",p.city)
    fmt.Println("State",p.state)
}
```

在上述代码中，我们使用了语法`p.city`和`p.state`,访问提升字段`city`和`state`就像它们是在结构体`p`中声明的一样。该程序输出：

```
Name: Naveen  
Age: 50  
City: Chicago  
State: Illinois
```

## 14.11 导出结构体和字段

如果结构体名称以大写字母开头，则它是其他包可以访问的导出类型。同样，如果结构体里的字段首字母大写。它也能被其他包访问到。下面我们通过一个示例来更好的理解。

在go工作区的src目录中，创建一个名为`struct`的文件夹，另外在`struct`文件夹中在创建一个目录`computer`.

在computer目录中，在名为spec.go的文件中保存下面的程序。

```go
package computer
type Spec struct{
    Maker string
    model string
    Price int
}
```

上述代码片段中，创建了一个computer包，里面有一个导出结构体类型Spec。Spec有两个导出字段Maker和Price，和一个未导出的字段model，接下来我们会在main包中导入这个包，并使用Spec结构体。

```go
package main
import "struct/computer"
import "fmt"
func main(){
    var spce computer.Spec
    spec.Maker="apple"
    spec.Price=50000
    fmt.Println("Spec:",spec)
}
```

包结构如下所示：

```
src  
   structs
        computer
            spec.go
        main.go
```

在上述程序中，我们导入了`computer`包，之后我们访问结构体`Spec`的两个导出字段`Maker`和`Price`。执行命令`go install struct`和`workspacepath/bin/struct`,运行该程序。

如果我们试图访问未导出的字段`model`,编译器会报错。

## 14.12 结构体相等性

** 结构体是值类型。如果它的每一个字段都是可比较的，则该结构体也是可比较的。如果两个结构体变量的对应字段相等，则这两个变量也是相等的。

```go
package main
import "fmt"

type name struct{
    firstName string
    lastName string
}

func main(){
    name1:=name{"Steve","Jobs"}
    name2:=name{"Steve","Jobs"}
    if name1==name2{
        fmt.Println("name1 and name2 are equal")
    }else{
        fmt.Println("name1 and name2 are not equal")
    }
    name3:=name{firstName:"Steve",lastName:"Jobs"}
    name4:=name{}
    name4.firstName="Steve"
    if name3==name4{
        fmt.Println("name3 and name4 are equal")
    }else{
        fmt.Println("name3 and name4 are not equal")
    }
    
}
```

在上述代码中，结构体类型`name`包含两个`string`类型，由于字符是可比较的，因此可以比较两个结构体变量。

则输出：

```
name1 and name2 are equal  
name3 and name4 are not equal
```

**如果结构体包含不可比较的字段，则结构体变量也不可比较**

```go
package main
import "fmt"
type image struct{
    data map[int]int
}

func main(){
    image1:=image{data:map[int]int{
        0:255,
    }}
    image2:=image{data:map[int]int{
        0:155,
    }}
    if image1==image2{
        fmt.Println("image1 and image2 are equal")
    }
}
```

在上述代码中，结构体类型`image`包含一个`map`类型的字段。由于`map`类型不可比较，因此两个结构体也不能进行比较。

# 15.方法

## 15.1 什么是方法

方法其实就是一个函数，在func这个关键字和方法名中间加入了一个特殊的接收器类型。接收器可以是结构体类型或者是非结构体类型。接收器是可以在方法的内部访问的。

语法：

```go
func(t Type)methodName(parameter list){
    
}
```

上面的代码创建了一个接收器类型为Type的方法`methodName`。

**示例**

```go
package main
import "fmt"
type Employee struct{
    name string
    salary int
    currency string
}

func (e Employee)displaySalary(){
    fmt.Printf("salary of %s is %s%d",e.name,e.currency,e.salary)
}
func main(){
    emp1:=Employee{
        name:"Sam Adolf",
        salary:5000,
        currency:"$",
    }
    emp1.displaySalary()
}
```

在上述程序中，我们在`Employee`结构体类型中创建了一个`displaySalary`方法。displaySalary（）方法在方法的内部访问了接收器`e Employee`。我们使用接收器`e`，并打印employee的name、currency和salary三个字段。

## 15.2 为什么需要方法

在下述函数中，我们只使用函数，不使用方法。

```go
package main
import "fmt"
type Employee struct{
    name string
    salary int
    currency string
}

func displaySalary(e Employee){
    fmt.Printf("Salary of %s is %s%d",e.name,e.currency,e.salary)
}
func main(){
    emp1:=Employee{
        name:"Sam Adolf",
        salary:5000,
        currency:"$",
    }
    displaySalary(emp1)
}
```

在上述程序中，`displaySalary`方法被转化为一个函数，`Employee`结构体被当做参数传递，输出同样的结果。

既然能够利用函数得到同样的结果，那我们为什么需要方法呢？

1. **go语言不是纯粹的面向对象的编程语言，**而且go不支持类，因此，基于类型的方法是一种实现和类相似行为的途径。
2. 相同的名字的方法可以定义在不同的类型上，而相同名字的函数时不被允许的，假设我们有一个`Square`和`Circle`结构体，可以在`Square`和`Circle`上分别定义一个`Area`方法。

```go
package main
import "fmt"
import "math"

type Rectangle struct{
    length int
    width  int
}
type Circle struct{
    radius float64
}
func (r Rectangle)Area()int{
    return r.length*r.width
}
func (c Circle)Area()float64{
    return math.Pi*c.radius*c.radius
}

func main(){
    r:=Rectangle{
        length:10,
        width:5,
    }
    fmt.Printf("Area of rectangle %d\n",r.Area())
    c:=Circle{
        radius:12,
    }
    fmt.Printf("Area of circle %f",c.Area())
}
```

输出结果:

```GO
Area of rectangle 50
Area of circle 452.389342
```

## 15.3 指针接收器与值接收器

除了可以使用值接收器的方法外，我们还可以创建指针接收器。两者的区别在于，指针接收器的方法内部的改变对于调用者是可见的，然而值接收器不可见。

```go
package main
import "fmt"
type Employee struct{
    name string
    age  int
}
//使用值接收器
func (e Employee)changeName(newName string){
    e.name=newName
}

//使用指针接收器
func (e *Employee)changeAge(newAge int){
    e.age=newAge
}

func main(){
    e:=Employee{
        name:"Mark Andrew",
        age:50,
    }
    fmt.Printf("Employee name before change %s",e.name)
    e.changeName("Michael Andrew")
    fmt.Printf("\nEmployee name ager change:%d",e.age)
    (&e).changeAge(51)
    fmt.Printf("\nEmployee age after change %d",e.age)
}
```

在上述程序中，`changeName`方法有一个值接收器`(e Employee)`,而`changeAge`方法有一个指针接收器`(e *Employee)`。在`changeName`方法中对`Employee`结构体的字段`name`所做的改变对调用者是不可见的，因此程序在调用`e.changeName("Michael Andrew")`这个方法的前后打印出相同的名字。由于`changeAge`方法是使用指针(e *Employee)接收器的，所以在调用`(&e).changeAge(51)`方法对age字段做出的改变对调用者是可见的。

输出为：

```
Employee name before change: Mark Andrew
Employee name after change: Mark Andrew

Employee age before change: 50
Employee age after change: 51
```

在上述程序中，我们使用`(&e).changeAge(51)`来调用changeAge方法，由于changeAge方法有一个指针接收器，所以我们使用&e来调用这个方法。其实，我们也可以直接通过e.changeAge（51）。

重写程序：

```go
package main
import "fmt"

type Employee struct{
    name string
    age  int
}
//使用值接收器的方法
func (e Employee)changeName(newName string){
    e.name=newName
}
//使用指针接收器
func (e *Employee)changeAge(newAge int){
   e.age=newAge 
}

func main(){
    e:=Employee{
        name:"Mark Andrew",
        age:50,
    }
    fmt.Printf("Employee name before change:%s",e.name)
    e.changeName("Michael Andrew")
    fmt.Printf("\nEmployee name after change:%s",e.name)
    fmt.Printf("\n\nEmployee age before change:%d",e.age)
    e.changeAge(51)
    fmt.Printf("\nEmployee age after change %d",e.age)
}
```

## 15.4 指针接收器？值接收器？

一般来说，指针接收器可以使用在：**对方法内部的接收器所做的改变应该对调用者可见时。**

指针接收器也可以被使用在如下场景：当拷贝一个结构体的代价过于昂贵时。考虑下一个结构体有很多的字段。在方法内使用这个结构体作为值接收器需要拷贝整个结构体。这是很昂贵的，在这样情况下使用指针接收器，结构体不会被拷贝，只会传递一个指针到方法内部使用。

在其他情况下，值接收器都可以被使用。

## 15.5 匿名字段的方法

数据结构体的匿名字段的方法可以被直接调用，就好像这些方法是数据定义了匿名字段的结构体一样。

```go
package main
import "fmt"

type address struct{
    city string
    state string
}
func(a address)fullAddress(){
    fmt.Printf("Full address:%s,%s",a.city,a.state)
}
type person struct{
    firstName string
    lastName string
    address
}
func main(){
    p:=person{
        firstName:"Elon",
        lastName:"Musk",
        address:address{
            city:"Los Angeles",
            state:"California",
        },
    }
    p.fullAddress()
}
```

在上述程序中，我们通过使用p.fullAddress()来访问address结构体的fullAddress（）方法，明确的调用p.address,fullAddress()是没有必要的，该程序输出：

```
Full address: Los Angeles, California
```

## 15.6 在方法中使用接收器与在函数中使用值参数

当一个函数有一个值参数，它只能接受一个值参数。

当一个方法有一个值接收器，它可以接受值接收器和指针接收器。

下面通过例子来解释：

```go
package main
import "fmt"
type rectangle struct{
    length int
    width  int
}
func area(r rectangle){
    fmt.Printf("Area Function result:%d\n",(r.length*r.width))
}
func (r rectangle)area(){
    fmt.Printf("Area Method result:%d\n",(r.length*r.width))
}
func main(){
    r:=rectangle{
        length:10,
        width:5,
    }
    area(r)
    r.area()
    p:=&r
    p.area()
}
```



