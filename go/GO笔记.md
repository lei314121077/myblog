
# 第三方包

## [glide](https://glide.sh/)

   一个golang项目包管理工具[github](https://github.com/Masterminds/glide)地址，[文档](https://glide.readthedocs.io/en/latest/commands/)地址
   
# IDE

## mac osx 安装 IDE

  这里我选择的是用*LITEIDE*,而我的笔记本上装的是双系统，linux和Windows，公司和我的个人台式机都是MAC OSX，然而如果我们是用
  包安装的话可以在[这里下载](http://golangtc.com/download/liteide) 包
  
  * install LiteIDE on Mac OSX
  
    1. 打开shell命令行，首先安装好home brew,可以在 [这里] (http://brew.sh/) 查看怎么安装。
      
      ```
        $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
      ```
    2.再到shell输入下面这条命令，p拍Enter键
    
      ```
        $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null ; brew install caskroom/cask/brew-cask 2> /dev/null
      ```
    3.ok后再输入这条命令，按Enter键
    
      ```
        $ brew cask install liteide
      ```
      [参考] (http://macappstore.org/liteide/)
    
  * install LiteIDE on Linux Ubuntu 14.04
  
    安装情况可以[参考这里](http://studygolang.com/articles/3267)
    

  * install LiteIDE on Windows
  
  # 一些概念和技巧
  * go语言里面是不允许声明的对象未被引用的，否则会报错
    
      ```go
      package main

      import "fmt"
     
      func main(){
        var a,b,c string
        fmt.Println("print a and b:", a, b) //这里我并没有把已声明的变量c引用，所以是会报错，因为GO里面不允许出现未被应用的对象占用内存
      }
      ```

  * 对于 String 中单个字符的操作会导致编译失败。String 是带有一些附加属性的只读的字节片（Byte Slices）。所以如果想要对 String 操作的话，应当使用字节片操作，而不是将它转换为 String 类型。
  
      ```go
      package main

      import "fmt"

      func main() {  
          x := "text"
          xbytes := []byte(x)
          xbytes[0] = 'T'

          fmt.Println(string(xbytes)) //prints Text
      }
      ```



# 一些规范

# Go开发规范

[Build web application with golang](https://github.com/astaxie/build-web-application-with-golang)

## Go framework

* [Beego](https://github.com/astaxie/beego)

## Contributing

1. 新功能基于`develop`分支建立新的分支，命名为`feature/...`
2. 编写单元测试文件，测试文件命名：`*_test.go`
3. 如果更改了接口，需要更新文档
4. 提交前
  * 测试正常通过
  * 规定的命名规则
  * 一个PR不要超过两个commit，如果超过两个，请先squash它们
5. Pull Request

## Go CodeReviewComments

Go 的代码审查建议，更多可以查看[https://github.com/golang/go/wiki/CodeReviewComments](https://github.com/golang/go/wiki/CodeReviewComments)

* 使用两个空格的缩进

  ```go
  func main() {
    fmt.Println("hello")
  }
  ```

* 命名

  文件夹和文件命名全部使用小写，单词使用下划线分割`print_test.go`

  ```go
  // print.go ✓ 好
  // Print.go ✗ 不好
  // print_test.go // ✓ 好
  ```

  Go 固定命名，公开函数首字母大写，包内函数首字母小写，全部使用驼峰命名

  ```go
  func Fprint() string {} // ✓ 好
  func tooLarge() string {} // ✗ 不好
  ```

  测试文件固定命名加`_test.go`

* 不要使用 Panic

  看[https://golang.org/doc/effective_go.html#errors](https://golang.org/doc/effective_go.html#errors)，不要使用`panic`用于正常的错误处理。使用`error`和多个返回值。

* Handle Errors 错误信息

  错误信息不应该大写（除非是专有名词或是首字母缩写）或是以标点符号结束。因为它们通常在其他上下文中打印。

  ```go
  fmt.Errorf("something bad") // ✓ 好
  fmt.Errorf("Something bad") // ✗ 不好
  ```

* 处理错误

  看 [https://golang.org/doc/effective_go.html#errors](https://golang.org/doc/effective_go.html#errors)。不要使用`_`变量丢弃错误。如果一个函数返回一个错误，检查它确保函数式正常运行。处理这个错误，并返回它或是在真正的异常情况下使用`panic`。

  一些语言通常在函数中返回不同的值来表示错误或者丢失结果。

* In-Band Errors

  ```go
  // 根据 key 查找键值 value，如果查不到则返回空 ""
  func Lookup(key string) string
  ```

  Go 支持多个返回值，这需要调用者来检查是否有错误，一个函数需要返回一个而外的值来表示其他值是有效的。这个返回值可能是错误(error)，或者不需要解释时可以使用布尔值。这个值通常在所有返回值的最后。

* Imports

  imports 是以组的形式组织的，在它们之间使用空行，标准包在第一组。

  ```go
  package main

  import (
    "fmt"
    "os"

    "appengine/user"
    "appengine/foo"

    "github.com/foo/bar"
  )
  ```

  goimports 可以帮助你处理这个。

* Import Dot

  import . 在测试中非常有用，由于循环依赖，不能成为被测试的包的一部分。

  ```go
  package foo_test

  import (
    . "foo"
    "bar/testutil" // 也导入了 "foo"
  )
  ```

  在这个例子中，测试文件不能在`foo`包中，因为它使用`bar/testutil`，它也引入`foo`，因此我们使用`import .`形式来伪装成`foo`包的一部分，即使它不是。处理这种情况，不要在你的程序中使用`import .`。它会使得你的程序难以阅读，因为它是难以理解的。

* 错误判断处理

  在一个最小的代码缩进中尝试保存正常的代码路径，和缩进错误处理，首先处理错误。这样做提升了程序的可读性，这个符合视觉的快速扫描习惯。

  ```go
  // ✗ 不好
  if err != nil {
    // error handling
  } else {
    // normal code
  }
  // ✓ 好
  if err != nil {
    // error handling
    return // or continue, etc.
  }
  // ✓ 好
  if x, err := f(); err != nil {
    // error handling
    return
  } else {
    // use x
  }
  // ✓ 好
  x, err := f()
  if err != nil {
    // error handling
    return
  }
  // use x
  ```

* 首字母缩写

  ```go
  var URL string // ✓ 好
  var url = "" // ✓ 好
  var Url string // ✗ 不好
  var ServeHTTP server // ✓ 好
  var ServeHttp server // ✗ 不好
  ```

* 接口

  TODO

* 结果参数命名

  考虑下这个在godoc应该是看起来像什么，比如：

  ```go
  func (n *Node) Parent1() (node *Node)
  func (n *Node) Parent2() (node *Node, err error)
  ```

  更好的用法是：

  ```go
  func (n *Node) Parent1() *Node
  func (n *Node) Parent2() (*Node, error)
  ```

  另外一种情况，如果一个函数返回了两个或是三个相同类型的参数，或者如果一个结果的含义通过上下文不清楚，添加命名会非常有用，比如：

  ```go
  func (f *Foo) Location() (float64, float64, error)
  ```

  没有下面这个清晰：

  ```go
  // Location returns f's latitude and longitude.
  // Negative values mean south and west, respectively.
  func (f *Foo) Location() (lat, long float64, err error)
  ```

* 包注释

  包注释，像所有注释一样由 godoc 展示，必须紧跟着包定义，中间没有空行

  ```go
  // Package math provides basic constants and mathematical functions.
  package math
  ```

  ```go
  /*
  Package template implements data-driven templates for generating textual
  output such as HTML.
  ....
  */
  package template
  ```

* 有用的测试失败

  测试失败需要输出有用的信息来显示哪里出错，输入是什么，返回是什么，预计返回什么。

* 变量命名

  在 Go 中的变量名应该短而不是长。对于空间有限的局部变量更是如此。例如 c 表示行数，i 表示索引。
  
## Build

```sh
# 编译到 linux 64bit
$ GOOS=linux GOARCH=amd64 go build
# 或者可以使用 -o 选项指定生成二进制文件名字
$ GOOS=linux GOARCH=amd64 go build -o app.linux

# 编译到 linux 32bit
$ GOOS=linux GOARCH=386 go build

# 编译到 windows 64bit
$ GOOS=windows GOARCH=amd64 go build

# 编译到 windows 32bit
$ GOOS=windows GOARCH=386 go build

# 编译到 Mac OS X 64bit
$ GOOS=darwin GOARCH=amd64 go build
```



# [一些开源的项目](http://blog.csdn.net/hackstoic/article/details/52008307)






