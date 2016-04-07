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
2. 导入包  package main
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
  
3. 声明包  import fmt
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

4. 打印 fmt.Println
  ```go
   package main
   import (
    "fmt"
   )
   
   func main(){
     fmt,PrintLn("see your agin !")      //换行打印
     fmt.Print("see your agin!")         //普通打印
   }
  ```
  > [更详细的介绍可以参考这里](http://www.jianshu.com/p/8be8d36e779c) 或者参考[官方文档](http://golang-examples.tumblr.com/post/86795367134/fmtprintf-format-reference-cheat-sheet)  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

