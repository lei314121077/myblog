# 简介

  beego 是一个快速开发 Go 应用的 HTTP 框架，他可以用来快速开发 API、Web 及后端服务等各种应用，是一个 RESTful 的框架，主要设计灵感来源于 tornado、sinatra 和 flask 这三个框架，但是结合了 Go 本身的一些特性（interface、struct 嵌入等）而设计的一个框架。且在一些比较大的网站例如youtube、360、有道、新浪、土豆、盛大、美团、腾讯都在用go来做服务器后台的一些开发。


## 为什么选Beego

  首先一个很重要的原因是在三年前，我就开始接触GO和Python当时带我的师傅（一个十几年开发经验的大牛“峰哥”）介绍下我开始接触，但是后面因为项目一直用的是Python以及自己创业就把对Go的研究一直拖勒一段日子，大概1年多的时间吧。选择Beego的原因有很多。
  * tornado、flask这2个Python的WEB框架我本身就非常熟悉，且我主导的几个项目都是用Tornado来做分布式服务器后台的所以这算是一个原因。
  * 支持国产，支持国产、支持国产。重要的事情说三遍！我是一个强烈的爱国主义者！！！
  * 也是最重要的一点，性能、文档、资料各方面都比较多。
  
## 对比

    [参考](http://studygolang.com/topics/466)
    
    
# Beego设计思路
  
  基本的设计思路是基于tornado、flask、sinatra的一些架构设计上的思路，然后集合GO语言本身设计出的一个http框架，主要应用领域包括api服务、服务器后台、任务调度、日志分发、游戏开发等领域。

# Beego基础应用笔记
  
## 下载、安装
  
  *  Mac osx (前提是你需要先安装好了go)
  
    home brew 安装 go语言程序包
    *  brew install go
    
    go语言安装包的形式安装Beego这个http框架
    * go get github.com/astaxie/beego
    
  *  linux(前提是你需要先安装好了go)
  
    安装 go语言程序包
    * sudo apt-get install go
    
    go语言安装包的形式安装Beego这个http框架
    * go get github.com/astaxie/beego

## 更新、安装
  Go 更新包的形式更新Beego
  * 更新

    go get -u github.com/astaxie/beego
    
  覆盖到 $GOPATH/src/github.com/astaxie/beeg 然后通过本地安装来执行
  * 安装
  
    go install  github.com/astaxie/beego   
  
## bee 命令详解

  * new 命令

    > new 命令是新建一个 Web 项目，我们在命令行下执行*bee new <项目名>*就可以创建一个新的项目。但是注意该命令必须在 
    > $GOPATH/src 下执行。最后会在 $GOPATH/src 相应目录下生成如下目录结构的项目  
  
  * api 命令 

    > 上面的 new 命令是用来新建 Web 项目，不过很多用户使用 beego 来开发 API 应用。所以这个 api 命令就是用来创建 API 
    > 应用的，执行命令之后如 *bee api <项目名>*  同样，必须在$GOPATH/src相对应的目录下生成。
  
  *  run 命令
      
    > 在开发 Go 项目的时候最大的问题是经常需要自己手动去编译再运行，*bee run* 命令是监控 beego 的项目，通过 
    > [fsnotify](https://github.com/howeyc/fsnotify)
    > 监控文件系统。但是注意该命令必须在$GOPATH/src/下的当前项目目录下才能执行。打开浏览器就可以看到基础页面了 http://localhost:8080/:

  * pack 命令
  
    > *bee pack*目录用来发布应用的时候打包，会把项目打包成zip包，这样我们部署的时候直接把打包之后的项目上传，解压就可以部署了
  
  * bale 命令
    
    > 这个命令目前仅限内部使用，具体实现方案未完善，主要用来压缩所有的静态文件变成一个变量申明文件，全部编译到二进制文件里面，用户发布的时候携带静态文件，包括 js、css、img 和 views。最后在启动运行时进行非覆盖式的自解压。

  
  *  version 命令
  
    > *bee version* 这个命令是动态获取bee、beego和Go的版本，这样一旦用户出现错误，可以通过该命令来查看当前的版本
  
   
  * generate 命令
    
    > 这个命令是用来自动化的生成代码的，包含了从数据库一键生成model，还包含了scaffold的，通过这个命令，让大家开发代码不再慢

  * migrate 命令
  
    > 这个命令是应用的数据库迁移命令，主要是用来每次应用升级，降级的SQL管理。
  
  * bee 工具配置文件
   
    您可能已经注意到，在 bee 工具的源码目录下有一个 *bee.json* 文件，这个文件是针对 bee 工具的一些行为进行配置。该功能还未完全开发完成，不过其中的一些选项已经可以使用：

    > "version": 0：配置文件版本，用于对比是否发生不兼容的配置格式版本。
    > "go_install": false：如果您的包均使用完整的导入路径（例如：github.com/user/repo/subpkg）,则可以启用该选项来进行 go 
    > install 操作，加快构建操作。
    > "watch_ext": []：用于监控其它类型的文件（默认只监控后缀为 .go 的文件）。
    > "dir_structure":{}：如果您的目录名与默认的 MVC 架构的不同，则可以使用该选项进行修改。
    > "cmd_args": []：如果您需要在每次启动时加入启动参数，则可以使用该选项。
    > "envs": []：如果您需要在每次启动时设置临时环境变量参数，则可以使用该选项。
    
    
  
  
  
  
  
  
  
  




