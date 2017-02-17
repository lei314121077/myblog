# 简介
   
   ```
 	golang官方并没有明确的明确的最佳方案给到我们，go语言的包是没有中央库统一管理的，通过使用go get命令从远程代码库(github.com,goolge code 等)拉取，直接跳过中央版本库的约束，让代码的拉取直接基于源代码版本控制库，开发者间的协同直接依赖于源代码的版本控制。直接去除了库版本的概念。没有明显的包版本标识，感觉还是有点不适应，官方的建议是把外部依赖的代码全部复制到自己可控的源代码库中，进行统一的管理。从而做到对依赖包的可控管理。我问了很多业内的朋友以及找了很多资料，其实有很多第三方的解决方案，今天同事跟我提了一下glide于是我研究了一下，并且感觉效果还不错，就打算把它集成到我的项目里面去。
   ```

# [glide](https://github.com/Masterminds/glide)

   * [document](http://glide.readthedocs.io/en/stable/?badge=stable) 

   * 安装

      ```sh
         go get github.com/Masterminds/glide
         curl https://glide.sh/get | sh

      ```

   * 命令介绍
      
      * glide create|init 初始化项目并创建 glide.yaml文件,glide.yaml格式
        如下
        
         ```
            package: github.com/appleboy/gorush
            import:
            - package: gopkg.in/yaml.v2
            - package: gopkg.in/redis.v3
            - package: github.com/Sirupsen/logrus
             version: v0.10.0
            - package: github.com/appleboy/gin-status-api
            - package: github.com/fvbock/endless
            - package: github.com/gin-gonic/gin
            - package: github.com/google/go-gcm
            - package: github.com/sideshow/apns2
             subpackages:
             - certificate
             - payload
            - package: github.com/stretchr/testify
            - package: github.com/asdine/storm
            - package: github.com/appleboy/gofight
            - package: github.com/buger/jsonparser
         ```

      * glide get 获取单个包

　　      * --all-dependencies 会下载所有关联的依赖包

　　      * -s 删除所有版本控制，如.git

　　      * -v 删除嵌套的vendor

      * glide install 安装包

         ```golang
            //下载包
            glide get github.com/mattn/go-adodb
            glide get --all-dependencies -s -v github.com/mattn/go-adodb
            //下载指定版本号的包
            glide get github.com/go-sql-driver/mysql#v1.2
         ```

      * glide update|up 更新包
   
   * 团队开发下的应用 

      在团队开始时，需要将 glide.yaml 和 glide.lock 进行版本控制，vendor 忽略掉。

      * 模拟下团队开发的流程

         A同学：初始化项目，并提交了源码，其中glide.yaml 和 glide.lock的内容如下
      
      ```
      glide.yaml:
          package: glide_demo6
          import:
          - package: github.com/mattn/go-adodb
          - package: github.com/go-ole/go-ole
      glide.lock:
          hash: 18e3b9c2f5c11f3268b22ebdbea09636c5cae28e78f0011578f455c485e9d214
          updated: 2016-05-18T23:43:15.8217224+08:00
          imports:
          - name: github.com/go-ole/go-ole
            version: 572eabb84c424e76a0d39d31510dd7dfd62f70b2
          - name: github.com/mattn/go-adodb
            version: 452cccbbcfb7906b3cbc512992557c1083e1011b
          devImports: []
       ```
       > B同学：拉去项目，执行 glide install，会自动下载对应的包

 
 # 参考

    * [glide包管理](http://studygolang.com/articles/7129)
    * [Golang的包管理之道](http://www.infoq.com/cn/articles/golang-package-management)
    * [Golang 套件管理工具 Glide](http://studygolang.com/topics/1629)

