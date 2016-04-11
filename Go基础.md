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
  
    3.3. 空标识符“_”是一个占位符，用于赋值操作的时候，丢弃、忽略某个值。通常这样用：

  > go的方法一般会返回2个值，一个通常的返回、一个错误标识。如 fmt.Println(x)会返回2个值，一个是打印的字节数，一个是相应的error值，那么 count,_ = fmt.Println(x) 这行代码就忽略了相应的error值。

3. 导入包  package main
  * 导入路径是对应包在 $GOROOT/pkg/$GOOS_$GOARCH/、$GOPATH/pkg/$GOOS_$GOARCH/ 或当前路径中的相对路径
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
  >注意这里在导入包的时候包名需要以双引号引起来 ""
  
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

  
8. 数组 Array

9. 切片 Slice

10. 字典 Map

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
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

