# <center>GAEDevelopment</center>


# 目录

  * [Google App Engine是什么?](#Google App Engine是什么?)
    * [功能支持](#功能支持)
    * [准备工作](#准备工作)
    * [GAE命令](#GAE命令)

# Google App Engine是什么?
  
  Google App Engine（GAE） 提供一整套开发组件来让用户轻松地在本地构建和调试网络应用，之后能让用户在Google强大的基础设施上部署和运行网络应用程序。配置可随应用的访问量和数据存储需要的增长轻松扩展，使用 GAE，将不再需要维护服务器：只需上传你的应用程序，它便可立即为你的客户提供服务。<br>

  简单来说，这和虚拟主机服务类似，只是运行环境不同。虚拟主机支持的是ASP, JSP, PHP等网页应用，而GAE现支持Java、Python和Google自家开发的Go这三种语言开发的应用程序，并为这三种语言提供基本相同的功能和API。<br>

  > GAE提供大量的免费使用额度和灵活的资费标准。多达 500 MB 的存储空间，以及可支持每月约 500 万页面浏览量的足够的 CPU 和带宽，完全免费。选择付费服务则可按需提高相应配置。

## 功能支持

  * 网址抓取（URL Fetch）：访问互联网上的资源，抓取检索数据。
  * 邮件（Mail）： GAE可以利用基于Gmail的基础设施来发送电子邮件。
  * Memcache缓存：高性能的内存缓存保障，对于那些不需要持久性存储和事务功能的数据（例如临时数据或从数据存储区复制到缓存以进行高速访问的数据）很有用。
  * 图像操作（Image Manipulation）：使用该 API，您可以对 JPEG 和 PNG 格式的图像进行缩放、裁剪、旋转和翻转，还能使用预先定义的算法提升图片的质量。
  * 计划任务和任务队列（Scheduled Tasks & Task Queues）：允许将任务计划为按指定间隔运行，这些任务通常称为Cron job。另外可以通过在一个队列插入任务（以Web Hook的形式）来实现后台处理，GAE会根据调度方面的设置来安排这个队列里面的任务执行。


## 准备工作
    
  * 拥有一个Google账户

    > 过程略过、、、、、

  * 下载开发环境所需的SDK 

    以下环境我是在mac上配置的

    * [go](https://cloud.google.com/appengine/docs/go/download)

      解压后配置以下环境变量，你也可以直接在你的zsh配置文件里面配置:

      ```go 

        export PATH=$PATH:DIRECTORY_PATH/go_appengine_sdk_OS_BIT-1.9.46/ 

      ``` 
    * [python](https://cloud.google.com/sdk/docs/)

      解压后输入以下命令:

      ```python 

        # 检查你的python版本
        python -V
        # 安装sdk
        ./google-cloud-sdk/install.sh
        # 初始化sdk
        ./google-cloud-sdk/bin/gcloud init
        # 学会使用gcloud --help
        ./google-cloud-sdk/bin

      ```

    * [java](https://cloud.google.com/appengine/docs/java/download)

      解压后输入以下命令:

      ```java

        # 配置环境变量
        export PATH=$PATH:DIRECTORY_PATH/appengine-java-sdk-1.9.46/bin/

        # App Engine Java SDK需要Java 7字节码级别。你可以使用Java 7或Java 8;一定要设置javac编译器标志来生成1.7字节码：
        -source 1.7 -target 1.7

      ```
      
## GAE命令
    
  * dev_appserver.py 项目   //名启动项目命令

  * dev_appserver.py --help  //帮助文档

## [Google云应用开发](https://cloud.google.com/appengine/downloads?csw=1)

  * 对接

    * python

    * go

    * java

## [Gmail开发](https://developers.google.com/gmail/api/guides/)

  * 对接

      * python

      * go

      * java

## [GoogleContacts联系人开发](https://developers.google.com/google-apps/contacts/v3/)

  * 对接

    * python
    
    * go
    
    * java
    
## [GoogleDrive云硬盘开发](https://developers.google.com/drive/)

  * [对接](https://developers.google.com/drive/v2/reference/)

    * [python](https://developers.google.com/drive/v3/web/quickstart/python)
    
    * [go](https://developers.google.com/drive/v3/web/quickstart/go)
    
    * [java](https://developers.google.com/drive/v3/web/quickstart/java)
  
    


