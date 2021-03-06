
# 第三方包

## monitor, mutex, lock有什么区别

* lock和Monitor的区别

一、lock的底层本身是Monitor来实现的，所以Monitor可以实现lock的所有功能。 
二、Monitor有TryEnter的功能，可以防止出现死锁的问题，lock没有。

* Mutex和其他两者的区别

个人测试三个都是在限制线程之外的互斥，线程之内，都不限制，同一个线程如果被lock两次。是不会出现死锁的。所以Mutex本身可以实现lock和Monitor所有的操作。至少从功能上讲是这样的。

但是Mutex是内核级别的，消耗较大的资源，不适合频繁的操作，会降低操作的效率。所以一般被调用部分的资源锁，常常用lock或者Monitor，可以提高效率。而线程和线程间的协调，可以用Mutex，因为相互互斥切换的机会会大大的降低，效率就不再那么的重要了。

Mutex本身是可以系统级别的，所以是可以跨越进程的。比如我们要实现一个软件不能同时打开两次，那么Mutex是可以实现的，而lock和monitor是无法实现的。

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
  
  * New和 Make的区别
     
     * new：
       
       用来初始化一个对象，并且返回该对象的首地址．其自身是一个指针．可用于初始化任何类型
     
     * make:
        
        返回一个初始化的实例，返回的是一个实例，而不是指针，其只能用来初始化：slice,map和channel三种类型
  * go 派生类型
     * (a) 指针类型（Pointer）
     * (b) 数组类型
     * (c) 结构化类型(struct)
     * (d) Channel 类型
     * (e) 函数类型
     * (f) 切片类型
     * (g) 接口类型（interface）
     * (h) Map 类型



# [一些开源的项目](http://blog.csdn.net/hackstoic/article/details/52008307)






