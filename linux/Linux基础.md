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


  * sudo & yum 提权
  
    ```
     # centos 系列
     $ yum 
     
     # ubuntu osx系列
     $ sudo 
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
  
