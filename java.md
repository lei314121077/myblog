# 重写java之回忆笔记
 
 妈蛋，说好的再也不写JAVA的呢！！！，时隔三年之后我又要重新拿起JAVA这门工具来写项目
 
## 安装 

 * 关于JAVA的常用工具
 
  * myeclipse 和 eclipse 
    
         > myeclipse要钱，eclipse不要钱。原来myeclipse只是一给eclipse做插件的，后来感觉用myeclipse插件的人多了，就把myeclipse插件和eclipse打包做成myeclipse产品

         > myeclipse是在eclipse上把java EE的一些插件封装起来了如hibernate，spring，ejb…… ,同时也有服务器插件如tomcat/weblogic/jboss等，如果做web开发是不错的选择。

         >  eclipse有几种不同的版本如classes标准版 ，这是eclipse的基础，如今eclipse也有对应ee版，可以与myeclipse抗衡，如果在添加jboss tools插件足够强大。

         > 如今如svn，hibernate tools JD……都插件是基于eclipse开发，但myeclipse都可以安装，应为它的核心就是eclipse。

         > 本人建议用eclipse，如果做Java EE （web）的开发可以下eclipse for EE 版，他集成了一些web服务器插件，你可以自己按照需求增加插件，足以超过myeclipse。


    
 * Mac 安装

    > 默认Mac是没有自带JAVA环境的，所以你需要自己安装，首先第一步是安装JDK,目前常用的几个版本有JDK1.6、JDK1.7、JDK1.8 .
    > 当然在 OS X 上，你可以同时安装多个版本的 JDK。你可以通过命令/usr/libexec/java_home -V来查看安装了哪几个 JDK。
   
    * /usr/libexec/java_home -V  查看安装了那几个JDK版本

       * [jdk1.6](https://support.apple.com/kb/DL1572?locale=zh_CN)
       * [jdk1.7](http://www.oracle.com/technetwork/cn/java/javase/downloads/jdk7-downloads-1880260.html)
       * [jdk1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

    * 在bash_profile里面添加环境变量

       > vi .bash_profile 输入以下内容  
       > vi .bash_profile 输入以下内容  
       > 然后执行source .bash_profile生效新配置  

       ```
          Mac默认 JDK 6（Mac默认自带了一个jdk6版本）  
          export JAVA_6_HOME=`/usr/libexec/java_home -v 1.6`  
          # 设置 JDK 7  
          export JAVA_7_HOME=`/usr/libexec/java_home -v 1.7`  
          # 设置 JDK 8  
          export JAVA_8_HOME=`/usr/libexec/java_home -v 1.8`  
          #默认JDK 6  
          export JAVA_HOME=$JAVA_6_HOME  
       ```

    * 使用Jenv 添加 JDK的版本

       ```
          $ jenv add /System/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home/
          $ jenv add /Library/Java/JavaVirtualMachines/jdk1.7.0_71.jdk/Contents/Home/
          $ jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0_25.jdk/Contents/Home/
       ```
   
    * 使用 jenv versions  查看添加的JDK版本
    
       ```
          $ jenv versions
       ```


# 基础理论

   * “被保护的成员”（protected）
   
  保护的意思表示存取它有条件限制以保护该成员，当您将类成员声明为受保护的成员之后，继承它的类就可以直接使用这些成员，但这些成员仍然受到对象范围的保护，不可被对象直接调用使用。
  
  
  
# 框架 

## Servlet

## Spring

## Struct

## Hibernate

## 注解
  
  
