# shell 
 
 * Ubuntu Linux系统环境变量配置文件：

      * /etc/profile : 
      
      在登录时,操作系统定制用户环境时使用的第一个文件 ,此文件为系统的每个用户设置环境信息,当用户第一次登录时,该文件被执行。
      
      * /etc /environment : 
 
           在登录时操作系统使用的第二个文件, 系统在读取你自己的profile前,设置环境文件的环境变量。
           
      * ~/.profile :  
      
           在登录时用到的第三个文件 是.profile文件,每个用户都可使用该文件输入专用于自己使用的shell信息,当用户登录时,该文件仅仅执行一次!默认情况下,他设置一些环境变量,执行用户的.bashrc文件。
           
      * /etc/bashrc : 
      
      为每一个运行bash shell的用户执行此文件.当bash shell被打开时,该文件被读取.
      * ~/.bashrc :
      
      该文件包含专用于你的bash shell的bash信息,当登录时以及每次打开新的shell时,该该文件被读取。
      
 * cat 查看
  
 ```
  # proc目录下记录的当前系统运行的各种数据,version记录的版本信息可以直接通过cat查看到，还可以看到我的gcc版本
  $ cat /proc/version
  
  # 查看自己的系统内核版本
  $ uname -a
  
  # 查看本机的系统版本信息，譬如说ubun14.4
  $ lsb_release -a
   
 ```


 * sudo 提权
 
 ```
  # centos 系列
  $ sudo yum install package-name
  
  # ubuntu osx系列
  $ sudo apt-get install package-name
 ```
 * cd
 
 * mkdir
 
 * touch
 
 * rm -r 
 
 *  解压安装包

 ```
  $ tar zxvf package
 ```

 * 安装包
 
 ```
  # centos
  $ yum install package-name 
  
  # ubuntu 
  $ sudo apt-get install package-name
  
  # osx 或者你可以装一个homebree
  $ sudo install package-name 
  $ bree install package-name
   
 ```
 * 更新包
 
 * 删除包
 
## apt的一些用法 （ubuntu软件管理包工具）

 * apt-get install <package>
  
  下载 <package> 以及所有倚赖的包裹,同时进行包裹的安装或升级.如果某个包裹被设置了 hold (停止标志,就会被搁在一边(即不会被升级)
  
  > sudo apt-get install # -----(package - - reinstall 重新安装包)
  
  > sudo apt-get -f install # -----(强制安装?#"-f = --fix-missing"当是修复安装吧...)
  

 * apt-cache search # ------(package 搜索包)
 
 * apt-cache show #------(package 获取包的相关信息，如说明、大小、版本等)

 * sudo apt-get remove #-----(package 删除包)
  
  移除 <package> 以及任何倚赖这个包裹的其它包裹.--purge 指明这个包裹应该被完全清除 (purged)
  
  > sudo apt-get remove - - purge # ------(package 删除包，包括删除配置文件等)
  
  > sudo apt-get autoremove --purge # ----(package 删除包及其依赖的软件包+配置文件等（只对6.10有效，强烈推荐）)
   

 * sudo apt-get update #------更新源
  
  升级来自 Debian 镜像的包裹列表,如果你想安装当天的任何软件,至少每天运行一次,而且每次修改了/etc/apt/sources.list 后,必须执行.

  * sudo apt-get upgrade #------更新已安装的包 apt-get upgrade [-u]

   升 级所以已经安装的包裹为最新可用版本.不会安装新的或移除老的包裹.如果一个包改变了倚赖关系而需要安装一个新的包裹,那么它将不会被升级,而是标志为 hold .apt-get update 不会升级被标志为 hold 的包裹 (这个也就是 hold 的意思).请看下文如何手动设置包裹为 hold .我建议同时使用 '-u' 选项,因为这样你就能看到哪些包裹将会被升级.

  * sudo apt-get dist-upgrade # ---------升级系统  apt-get dist-upgrade [-u]
   
  和 apt-get upgrade 类似,除了 dist-upgrade 会安装和移除包裹来满足倚赖关系.因此具有一定的危险性.
  
* sudo apt-get dselect-upgrade #------使用 dselect 升级
 
* apt-cache depends #-------(package 了解使用依赖)
* 
  > apt-cache rdepends # ------(package 了解某个具体的依赖?#当是查看该包被哪些包依赖吧...)

* sudo apt-get build-dep # ------(package 安装相关的编译环境)

* sudo apt-get source #------(package 下载该包的源代码)

* sudo apt-get clean && sudo apt-get autoclean # --------清理下载文件的存档 && 只清理过时的包

* sudo apt-get check #-------检查是否有损坏的依赖

# linux 服务器的一些应用
## scp是什么
 scp是secure copy的简写，用于在Linux下进行远程拷贝文件的命令，和它类似的命令有cp，不过cp只是在本机进行拷贝不能跨服务器，而且scp传输是加密的。可能会稍微影响一点点速度。但是相对于在服务器上搭FTP来说，用SCP命令在服务器与本地之间建立文件传输的通道还是比较方便的。
## scp有什么用？

 * 姿势一
  
  我们需要获得远程服务器上的某个文件，远程服务器既没有配置ftp服务器，没有开启web服务器，也没有做共享，无法通过常规途径获得文件时，只需要通过scp命令便可轻松的达到目的。

 * 姿势二
  
  我们需要将本机上的文件上传到远程服务器上，远程服务器没有开启ftp服务器或共享，无法通过常规途径上传是，只需要通过scp命令便可以轻松的达到目的。

## SCP的使用姿势

* 获取远程服务器上的文件

 ```
  scp -P 2222 root@14.185.28.41: /root/app.tar.gz /home/app.tar.gz
 ```
 上面写的参数大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数，或者省略掉2222。 root@14.185.28.41 表示使用root用户登录远程服务器14.185.28.41，:/root/app.tar.gz，表示远程服务器上的文件（你可以用pwd先看一下目录的具体路径然后再操作），最后面的/home/app.tar.gz表示保存在本地上的路径和文件名。还可能会用到p参数保持目录文件的权限访问时间等。

* 获取远程服务器上的文件夹
 
 ```
   scp -p -r /home/app.tar.gz root@41.185.28.41:/root
 ```
 上面写的参数大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。 /home/app.tar.gz表示本地上准备上传文件的路径和文件名。root@41.185.28.41表示使用root用户登录远程服务器
 41.185.28.41上面，:/root 表示保存在远程服务器上的root目录下，root后面加路劲表示具体的路劲和文件名。
 
* 上传文件到服务器
 
 ```
  scp -P 2222 root@14.185.28.41:/root/app.tar.gz /home/app.tar.gz
 ```
 上面写的参数大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。 root@14.185.28.41 表示使用root用户登录远程服务器14.185.28.41，:/root/app.tar.gz 表示远程服务器上的文件，最后面的/home/app.tar.gz表示保存在本地上的路径和文件名。还可能会用到p参数保持目录文件的权限访问时间等。

* 上传文件夹到服务器
 
 ```
  scp -P 2222 -r root@14.185.28.41:/root/odoo/ /home/odoo/
 ```
 上端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。-r 参数表示递归复制（即复制该目录下面的文件和目录）；root@14.185.28.41 表示使用root用户登录远程服务器14.185.28.41，:/root/odoo/ 表示远程服务器上的目录，最后面的/home/odoo/表示保存在本地上的路径。
 
 * 常用的几个参数
  
  ```
   -v 和大多数 linux 命令中的 -v 意思一样 , 用来显示进度 . 可以用来查看连接 , 认证 , 或是配置错误 .

   -C 使能压缩选项 .
   
   -4 强行使用 IPV4 地址 .
   
   -6 强行使用 IPV6 地址 .
  ```




