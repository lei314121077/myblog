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
















