# 简介
<p> GO语言诞生于2007年，据说当时是狗爹（Google）的几位大牛搞出来的Robert Griesemer, Rob Pike, 和 Ken Thompson。
GO语言是一门静态类型的语言，类似于C语言一样，他自带有类型收集，垃圾收集，动态输入，以及内置了对并发的支持。
还有丰富的标准库。</p>

#特点
<span>支持</span>
* 支持类型推断
* 天生支持高并发：轻量进程（通过够程），通道，select语句
* 编译快
* 简单安全、函数式编程
* 支持接口类和内嵌

<span>不支持</span>
* 不支持类型继承
* 不支持任何方法或运算符重载
* 不支持包之间循环依赖
* 不支持对指针运算
* 不支持断言
* 不支持泛型编程

# 数据类型
## 基础数据类型
  <table>
    <tr>
      <td>类型</td><td>取值范围</td><td>默认值</td><td>类型</td><td>取值范围</td><td>默认值</td>
    </tr>
    <tr>
      <td>int</td><td>int32,int64</td><td>0</td><td>uint</td><td>uint32,uint64</td><td>0</td>
    </tr>
    <tr>
      <td>int8</td><td>-27 ~ 27-1</td><td>0</td><td>uint8,byte</td><td>0 ~ 28-1</td><td>0</td>
    </tr>
    <tr>
      <td>int16</td><td>-215 ~ 215-1</td><td>0</td><td>uint16</td><td>0 ~ 216-1</td><td>0</td>
    </tr>
    <tr>
      <td>int32,rune</td><td>-231 ~ 231-1</td><td>0</td><td>uint32</td><td>uint32</td><td>0</td>
    </tr>
    <tr>
      <td>int64</td><td>-263 ~ 263-1</td><td>0</td><td>uint64</td><td>0 ~ 264-1</td><td>0</td>
    </tr>
    <tr>
      <td>float32</td><td>IEEE-754 32-bit</td><td>0.0</td><td>float64</td><td>IEEE-754 64-bit</td><td>0.0</td>
    </tr>
    <tr>
      <td>complex64</td><td>float32+float32i</td><td>0 + 0i</td><td>complex128</td><td>float64+float64i</td><td>0 + 0i</td>
    </tr>
    <tr>
      <td>bool</td><td>true,false</td><td>false</td><td>string</td><td>"" ~ "∞"</td><td>"",``</td>
    </tr>
    <tr>
      <td>uintptr</td><td>int32,int64</td><td>0</td><td>error</td><td>-</td><td>nil</td>
    </tr>
  </table>

  > byte 是 uint8 的别名
  
  > rune 是 int32 的别名，代表一个Unicode码点
  
  > int与int32或int64是不同的类型，只是根据架构对应32/64位值
  
  > uint与uint32或uint64是不同的类型，只是根据架构对应32/64位值 

# 语法

1. 注释   
  ```go
   package main
   import (
    "fmt"
   )
   
   func main(){
     /*
        块注释
     */
     // 行注释
   }
  ```  
2. 标识符

  > 可以这么说，除了数字开头的不允许，符号开头的不允许，关键字不允许，其他的Unicode字符组合都可以。“_33”也可以是标识符、“我们”也可以是标识符。标识符也区分大小写。

    2.1. 以大写字母开头的标识符是公开的。（这个很有意思）
  
    2.2. 其他任何标识符都是私有的。
  
    3.3. 空标识符“_”是一个占位符，用于赋值操作的时候，丢弃、忽略某个值。

  > 通常这样用：go的方法一般会返回2个值，一个通常的返回、一个错误标识。如 fmt.Println(x)会返回2个值，一个是打印的字节数，一个是相应的error值，那么 count,_ = fmt.Println(x) 这行代码就忽略了相应的error值。

3. 导入包  package main

  * 导入路径相对应包在 $GOROOT/pkg/$GOOS_$GOARCH/、$GOPATH/pkg/$GOOS_$GOARCH/ 或当前路径中的相对路径

 正确的姿势：

  ```go
   import "fmt"          // 导入官方标准库  
   import "a/b"          // 绝对路径导入
   import "./a/b"        //相对路径导入
   import "../a/b/c"     //相对路径导入
   import (              //官方姿势，导入标准库
     "fmt"
     "http"
   )
  ```
  
 错误的姿势：
 
  ```go
   import a/b/c
   import "a.b.c"
   import a.b.c
  ```
  
  > 注意这里在导入包的时候包名需要以双引号引起来 ""
  
4. 声明包  import fmt
  * 使用package关键字声明当前源文件所在的包
  * 包声明语句是所有源文件的第一行非注释语句
  * 包名称中不能包含空白字符
  * 包名必须与源文件所在的目录名称保持一致
  * 每个目录中只能定义一个package
  
  正确的申明姿势:

  ```go
  package main                      //申明一个main 包
  package my_tools_package          //申明一个自定义的工具包
  ```

 错误的申明姿势

  ```go
  package  "main"                  //错误
  package  a/b/c                   //错误
  package  a.b.c                   //错误

  ```

5. 打印 fmt.Println
  ```go
   package main
   import (
    "fmt"
   )
   
   func main(){
     fmt.PrintLn("see your agin !")      //换行打印
     fmt.Print("see your agin!")         //普通打印
   }
  ```
  
6. 变量  Variable
  * 在Go语言中，声明变量的正确姿势是使用 *var* 关键字，而无需赋初始值。 
  正确的姿势:
  ```go
  
  var i int        // i = 0   默认为0
  var s string     // s = ""  默认为空字符串，不为NULL即Go当中的Nil    
  var e error      // e = nil, error是Go的内建接口类型。
  
  var a,b,c int    // a, b, c = 0 var 还可以声明一个变量列表，类型放在变量名的后面
  
  var (
    a int          // a = 0
    b string       // b = ""
    c uint         // c = 0
    d,e,f int      // d,e,f = 0
  )
  
  var a = 'A'      // a int32
  
  a := 3
  a, b, c := 8, 'hello', true      //a = int b = string c = bool
  
  _, b := 7, 24   // _  = 丢弃，  b = 24
  ```
  
  小结:
  > 1、这里需要注意在Go中的string是值类型，默认零值是空串 "" 或 ``，不存在nil(null)值。  
  
  > 2、变量的命名规则，正确的姿势是 *var*关键字 + 变量名 + 类型 通常类型在后面。
  
  > 3、变量定义初始化时也可以省略类型，Go语言会自动根据初始化值推导出变量的类型。 
  
  > 4、符号:=定义并初始化变量，根据符号右边表达式的值的类型声明变量并初始化它的值，:=不能在函数外使用，函数外的每个语法块都必须以关键字开始 
  
  > 5、 _(下划线)是个特殊的变量名，任何赋予它的值都会被丢弃。另外_还可以在导入包的时候一起用，这样做的话他会忽略包中的所有内容但是他会执行包中的init()函数。
  
  
7. 常量  Constant
  * 常量可以是字符、字符串、布尔或数值类型的值，数值常量是高精度的值
    ```go
      const x int = 3
      const y,z int  = 1, 2
      const (
        a byte = 'A'
        b string = "B"
        c bool = true
        d int = 4
        e float32 = 5.1
        f complex64 = 6 + 6i
      )
      const a = 0        // a int
    ```
    
    * 根据常量值自动推导类型
    
    ```go
      const (
        b = 2.3             // b float64
        c = true            // c bool
        d = len("asdf")     // d = 4
        e                   // e = 4 常量组内定义的常量只有名称时，其值会根据上一次最后出现的常量表达式计算相同的类型与值
        f                   // f = 4
        g,h,i = 7,8,9       // 复用表达式要一一对应
        x,y,z               // x = 7, y = 8, z = 9
      )
    
    ```
    > 常量组内定义的常量只有名称时，其值会根据上一次最后出现的常量表达式计算相同的类型与值。
    
    * 自动递增枚举常量 iota
    
      > iota的枚举值可以赋值给数值兼容类型
      每个常量单独声明时，iota不会自动递增，只有当iota每次被引用或组合声明时才会逐步自增，初始值为0，自增值为1
    
    ```go
      const a int = iota        // a = 0
      const b int = iota        // b = 0
      const c byte = iota       // c = 0
      const d uint64 = iota     // d = 0
    ```
    * 常量组合声明时，iota每次引用会逐步自增，初始值为0，自增值为1
    
    ```go
      const (
         a uint8 = iota        // a = 0
         b int16 = iota        // b = 1
         c rune = iota         // c = 2
         d float64 = iota      // d = 3
         e uintptr = iota      // e = 4
      )
    ```
    * 即使iota不是在常量组内第一个开始引用，也会按组内常量数量递增
    
    ```go
      const (
          a = "A"
          b = 'B'
          c = iota    // c = 2
          d = "D"
          e = iota    // e = 4
      )
    ```
    
    * 枚举的常量都为同一类型时，可以使用简单序列格式(组内复用表达式).
    
    ```go
      const (
        a = iota     // a int32 = 0
        b            // b int32 = 1
        c            // c int32 = 2
      )
    ```
    * 枚举序列中的未指定类型的常量会跟随序列前面最后一次出现类型定义的类型.
    
    ```go
      const (
        a byte = iota    // a uint8 = 0
        b                // b uint8 = 1
        c                // c uint8 = 2
        d rune = iota    // d int32 = 3
        e                // e int32 = 4
        f                // f int32 = 5
      )
    ```
    > iota自增值只在一个常量定义组合中有效，跳出常量组合定义后iota初始值归0
    
    * 定制iota序列初始值与步进值 (通过组合内复用表达式实现)
    
    ```go
      const (
        a = (iota + 2) * 3    // a int32 = 6    (a=(0+2)*3) 初始值为6,步进值为3
        b                     // b int32 = 9    (b=(1+2)*3)
        c                     // c int32 = 12    (c=(2+2)*3)
        d                     // d int32 = 15    (d=(3+2)*3)
    )
    ```
  
8. 数组 Array
  数组的声明带有长度信息且长度固定，数组是值类型默认值不是nil，传递参数时会进行复制。
  正确的姿势：
  
  ```go
    var arr [n]type
  ```
  
  > 在[n]type中，n表示数组的长度，type表示存储元素的类型。对数组的操作和其它语言类似，都是通过[]来进行读取或赋值的譬如说JAVA 譬如说C语言。
  
  ```go
    var arr [10]int  // 声明了一个int类型的数组
    arr[0] = 42      // 数组下标是从0开始的
    arr[1] = 13      // 赋值操作
    fmt.Printf("The first element is %d\n", arr[0])  // 获取数据，返回42
    fmt.Printf("The last element is %d\n", arr[9]) //返回未赋值的最后一个元素，默认返回0
    
    a := [3]int{1, 2, 3} // 声明了一个长度为3的int数组
    
    b := [10]int{1, 2, 3} // 声明了一个长度为10的int数组，其中前三个元素初始化为1、2、3，其它默认为0
    
    c := [...]int{4, 5, 6} // 可以省略长度而采用`...`的方式，Go会自动根据元素个数来计算长度
  ```
  
  * 二维数组 & 嵌套数组
  
  > 使用 *...* 自动计算数组的长度
  
    ```go
  
      var length = [...]int{1,2,3,4,5}
      var a = [...]int{{1,2,3},{'a','b', 'c'},{'h','e','l','l','o'}}
    
      //多维数组只能自动计算最外围数组长度
      x := [...][3]int{{0, 1, 2}, {3, 4, 5}}
      y := [...][2][2]int{{{0,1},{2,3}},{{4,5},{6,7}}}
    
      //跟其他语言类似譬如说，C、JAVA、PYTHON，GO也是通过下标的方式去访问数组元素的
      fmt.Println(y[1][1][0])
    
      var arr = [5]{1，2，3，4，5}
    
      //range 关键字
      for key, val := range arr{
        fmt.PrintLn(key,val)  
      }
    
    ```
  >  未指定初始化的元素保持默认的零值

9. 切片 Slice
  * slice 切片是对一个数组上的连续一段的引用，并且同时包含了长度和容量信息,因为是引用类型，所以未初始化时的默认零值是nil，长度与容量都是0. slice是一个引用类型。 slice总是指向一个底层array，slice的声明也可以像array一样，只是不需要长度。
  正确的姿势: 
  ```go
    //  使用内置函数make初始化slice，第一参数是slice类型，第二参数是长度，第三参数是容量(省略时与长度相同)
    var b = make([]int, 0)
    fmt.Printf("%T\t%#v\t%d\t%d\n", b, b, len(b), cap(b))      // []int    []int{}    0    0
    
    var c = make([]int, 3, 10)
    fmt.Printf("%T\t%#v\t%d\t%d\n", c, c, len(c), cap(c))    // []int    []int{}    3    10

    var a = new([]int)
    fmt.Printf("%T\t%#v\t%d\t%d\n", a, a, len(*a), cap(*a))  // *[]int    &[]int(nil)    0    0
  ```
  
  1. cap()函数返回的是数组切片分配的空间大小。
  
  2. len()函数返回的是数组长度的大小。
  3. append 向slice里面追加一个或者多个元素，然后返回一个和slice一样类型的slice
  4. copy 函数copy从源slice的src中复制元素到目标dst，并且返回复制的元素的个数

  > 注：append函数会改变slice所引用的数组的内容，从而影响到引用同一数组的其它slice。 但当slice中没有剩余空间（即(cap-len) == 0）时，此时将动态分配新的数组空间。 返回的slice数组指针将指向这个空间，而原数组的内容将保持不变；其它引用此数组的slice则不受影响。
  
  * 下面是一个具体的示列，也是我们平时用的比较多的，具体情况跟Python的使用方式类似。
    
    ```go
      // 声明一个数组
      var array = [10]byte{'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'}
      // 声明两个slice
      var aSlice, bSlice []byte

      // 演示一些简便操作
      aSlice = array[:3] // 等价于aSlice = array[0:3] aSlice包含元素: a,b,c
      aSlice = array[5:] // 等价于aSlice = array[5:10] aSlice包含元素: f,g,h,i,j
      aSlice = array[:]  // 等价于aSlice = array[0:10] 这样aSlice包含了全部的元素

      // 从slice中获取slice
      aSlice = array[3:7]  // aSlice包含元素: d,e,f,g，len=4，cap=7
      bSlice = aSlice[1:3] // bSlice 包含aSlice[1], aSlice[2] 也就是含有: e,f
      bSlice = aSlice[:3]  // bSlice 包含 aSlice[0], aSlice[1], aSlice[2] 也就是含有: d,e,f
      bSlice = aSlice[0:5] // 对slice的slice可以在cap范围内扩展，此时bSlice包含：d,e,f,g,h
      bSlice = aSlice[:]   // bSlice包含所有aSlice的元素: d,e,f,g
    ```
    
   > slice是引用类型，所以当引用改变其中元素的值时，其它的所有引用都会改变该值，                例如上面的aSlice和bSlice，如果修改了aSlice中元素的值，那么bSlice相对应的值也会改变。

    从概念上面来说slice像一个结构体，这个结构体包含了三个元素：

    * 一个指针，指向数组中slice指定的开始位置
    * 长度，即slice的长度
    * 最大长度，也就是slice开始位置到数组的最后位置的长度
    
    ```go
      Array_a := [10]byte{'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'}
      Slice_a := Array_a[2:5]
    ```
    
  * 向slice中增加/修改元素
    
    ```go
      s := []string{}
      s = append(s, "a")              // 添加一个元素
      s = append(s, "b", "c", "d")    // 添加一列元素
      t = []string{"e", "f", "g"}
      s = append(s, t...}             // 添加另一个切片t的所有元素
      s = append(s, t[:2]...}         // 添加另一个切片t的部分元素

      s[0] = "A"                      // 修改切片s的第一个元素
      s[len(s)-1] = "G"               // 修改切片s的最后一个元素
    ```
    
  * 删除slice中指定的元素
    >  因为slice引用指向底层数组，数组的长度不变元素是不能删除的，所以删除的原理就是排除待删除元素后用其他元素重新构造一个数组
  
    ```go
      func deleteByAppend() {
          i := 3
          s := []int{1, 2, 3, 4, 5, 6, 7}
          //delete the fourth element(index is 3), using append
          s = append(s[:i], s[i+1:]...)
      }
      
      func deleteByCopy() {
          i := 3
          s := []int{1, 2, 3, 4, 5, 6, 7}
          //delete the fourth element(index is 3), using copy
          copy(s[i:], s[i+1:])
          s = s[:len(s)-1]
      }
    
    ```
  
10. 字典 Map
  * map是引用类型，使用内置函数 make进行初始化，未初始化的map零值为 nil长度为0，并且不能赋值元素
  正确的声明姿势:
  ```go
    //方式1  未赋值
    var dict1 map[int]int
    dict1[0] = 0
    
    //方式2  赋值
    var dict2 map[int]int = make(map[int]int)
    dict2[0] = 0                              // 插入或修改元素
    fmt.Printf("type: %T\n", dict2)           // map[int]int
    fmt.Printf("value: %#v\n", dict2)         // map[int]int(0:0)
    fmt.Printf("value: %v\n", dict2)          // map[0:0]
    fmt.Println("is nil: ", nil == dict2)     // false
    fmt.Println("length: ", len(dict2))       // 1

    //方式3  直接赋值初始化map
    m := map[int]int{
      0:0,
      1:1,                                  // 最后的逗号是必须的
    }
    n := map[string]S{
      "a":S{0,1},
      "b":{2,3},                            // 类型名称可省略
    }
  ```
  map的增加、读取、修改、删除操作
  
  ```go
    dict :=  map[string]S{
      "a":"hello",
      "b":"world",
    }
    
    dict["a"]             //读取dict中key值为"a"的元素的值。
    dict["c"] = "ok"      //向dict中添加key值为“c”，values值为“ok”的值。
    dict["b"] = "kitty"   //替换dict中key值为"b"的元素的值。
    delete(dict, "c")     //删除dict中key值为“c”的元素的值。
    
  ```
  
  
  使用map过程中需要注意的几点：
  > 1. map是无序的，每次打印出来的map都会不一样，它不能通过index获取，而必须通过key获取
  > 2. map的长度是不固定的，也就是和slice一样，也是一种引用类型
  > 3. 内置的len函数同样适用于map，返回map拥有的key的数量
  > 4. map的值可以很方便的修改，通过numbers["one"]=11可以很容易的把key为one的字典值改为11
  > 5. map和其他基本型别不同，它不是thread-safe，在多个go-routine存取时，必须使用mutex lock机制

  map的初始化可以通过key:val的方式初始化值，同时map内置有判断是否存在key的方式

11. 结构体 Struct

12. 指针 Pointer

13. 通道 Channel

14. 接口 Interface

15. 自定义类型
  
# 语句 Statement
## 分号/括号 ; {

## 条件语句 if

## 分支选择 switch

## 循环语句 for

## 通道选择 select

## 延迟执行 defer

## 跳转语句 goto

# 函数 Function

## 函数声明 Declare

## 函数闭包 Closure

## 内建函数 Builtin

## 初始化函数 init

## 方法 Method

# 并发 Concurrency

# 测试 Testing

## 单元测试 Unit

## 基准测试 Benchmark



# Web 基础回顾


  
  
  
  
  
  
  
  > [更详细的介绍可以参考这里](http://www.jianshu.com/p/8be8d36e779c) 或者参考[官方文档](http://golang-examples.tumblr.com/post/86795367134/fmtprintf-format-reference-cheat-sheet)  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

