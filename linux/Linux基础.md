# shell 
 
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
 



