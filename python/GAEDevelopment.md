# <center>GAEDevelopment</center>

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

  
  
  

