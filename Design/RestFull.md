[目录](#)
  * [REST简介](#REST简介)
  * [REST约束](#REST约束)
  * [要深入理解REST，需要理解REST的五个关键词](#要深入理解REST，需要理解REST的五个关键词)
  * [什么是超文本驱动？](#什么是超文本驱动？)
  * [简单性](#简单性)
  * [可伸缩性](#简单性)
  * [松耦合](#松耦合)
  * [API的演进](#API的演进)
    * [URL规范](#URI规范)
    * [Request 请求规范](#Request规范)
    * [Response 响应规范](#Response规范)


# REST简介

  > REST是设计风格而不是标准。REST通常基于使用HTTP，URI，和XML以及HTML这些现有的广泛流行的协议和标准。

  * 资源是由路由也就是URI来指定的。

  * 对资源的操作包括获取、创建、修改和删除资源，这些操作正好对应HTTP协议提供的GET、POST、PUT和DELETE方法。

  * 通过操作资源的表现形式来操作资源。

  * 资源的表现形式则是XML或者HTML，取决于读者是机器还是人，是消费web服务的客户软件还是web浏览器。当然也可以是任何其他的格式。

# REST约束
  
  REST架构风格最重要的架构约束有6个
  
  * 客户-服务器（Client-Server）
  
    > 通信只能由客户端单方面发起，表现为请求-响应的形式。

  * 无状态（Stateless）
    
    > 通信的会话状态（Session State）应该全部由客户端负责维护。

  * 缓存（Cache）
    
    > 响应内容可以在通信链的某处被缓存，以改善网络效率。

  * 统一接口（Uniform Interface）
    
    > 通信链的组件之间通过统一的接口相互通信，以提高交互的可见性。也就是我们同一个URL的不同操作，譬如（GET\POST\PUT\DELETE）等

  * 分层系统（Layered System）
    
    > 通过限制组件的行为（即，每个组件只能“看到”与其交互的紧邻层），将架构分解为若干等级的层。
  
  * 按需代码（Code-On-Demand，可选）
    
    > 支持通过下载并执行一些代码（例如Java Applet、Flash或JavaScript），对客户端的功能进行扩展。

# 要深入理解REST，需要理解REST的五个关键词

  * 资源（Resource）
 
  * 资源的表述（Representation）
 
  * 状态转移（State Transfer）
 
  * 统一接口（Uniform Interface）
 
  * 超文本驱动（Hypertext Driven）

    * 1 什么是资源？

      > 资源是一种看待服务器的方式，即，将服务器看作是由很多离散的资源组成。每个资源是服务器上一个可命名的抽象概念。因为资源是一个抽象的概念，所以它不仅仅能代表服务器文件系统中的一个文件、数据库中的一张表等等具体的东西，可以将资源设计的要多抽象有多抽象，只要想象力允许而且客户端应用开发者能够理解。与面向对象设计类似，资源是以名词为核心来组织的，首先关注的是名词。一个资源可以由一个或多个URI来标识。URI既是资源的名称，也是资源在Web上的地址。对某个资源感兴趣的客户端应用，可以通过资源的URI与其进行交互。

    * 2 什么是资源的表述？

      > 资源的表述是一段对于资源在某个特定时刻的状态的描述。可以在客户端-服务器端之间转移（交换）。资源的表述可以有多种格式，例如HTML/XML/JSON/纯文本/图片/视频/音频等等。资源的表述格式可以通过协商机制来确定。请求-响应方向的表述通常使用不同的格式。

    * 3 什么是状态转移？

      > 状态转移（state transfer）与状态机中的状态迁移（state transition）的含义是不同的。状态转移说的是：在客户端和服务器端之间转移（transfer）代表资源状态的表述。通过转移和操作资源的表述，来间接实现操作资源的目的。

    * 4 什么是统一接口？

      > REST要求，必须通过统一的接口来对资源执行各种操作。对于每个资源只能执行一组有限的操作。以HTTP/1.1协议为例，HTTP/1.1协议定义了一个操作资源的统一接口，主要包括以下内容：

## 7个HTTP方法：

  > GET/POST/PUT/DELETE/PATCH/HEAD/OPTIONS

  * HTTP头信息（可自定义）

  * HTTP响应状态代码（可自定义）

  * 一套标准的内容协商机制

  * 一套标准的缓存机制

  * 一套标准的客户端身份认证机制

  > REST还要求，对于资源执行的操作，其操作语义必须由HTTP消息体之前的部分完全表达，不能将操作语义封装在HTTP消息体内部。这样做是为了提高交互的可见性，以便于通信链的中间组件实现缓存、安全审计等等功能。

# 什么是超文本驱动？

  > “超文本驱动”又名“将超媒体作为应用状态的引擎”（Hypermedia As The Engine Of Application State，来自Fielding博士论文中的一句话，缩写为HATEOAS）。将Web应用看作是一个由很多状态（应用状态）组成的有限状态机。资源之间通过超链接相互关联，超链接既代表资源之间的关系，也代表可执行的状态迁移。在超媒体之中不仅仅包含数据，还包含了状态迁移的语义。以超媒体作为引擎，驱动Web应用的状态迁移。通过超媒体暴露出服务器所提供的资源，服务器提供了哪些资源是在运行时通过解析超媒体发现的，而不是事先定义的。从面向服务的角度看，超媒体定义了服务器所提供服务的协议。客户端应该依赖的是超媒体的状态迁移语义，而不应该对于是否存在某个URI或URI的某种特殊构造方式作出假设。一切都有可能变化，只有超媒体的状态迁移语义能够长期保持稳定。

  一旦读者理解了上述REST的五个关键词，就很容易理解REST风格的架构所具有的6个的主要特征：

  * 面向资源（Resource Oriented）

  * 可寻址（Addressability）

  * 连通性（Connectedness）

  * 无状态（Statelessness）

  * 统一接口（Uniform Interface）

  * 超文本驱动（Hypertext Driven）

  > 这6个特征是REST架构设计优秀程度的判断标准。其中，面向资源是REST最明显的特征，即，REST架构设计是以资源抽象为核心展开的。可寻址说的是：每一个资源在Web之上都有自己的地址。连通性说的是：应该尽量避免设计孤立的资源，除了设计资源本身，还需要设计资源之间的关联关系，并且通过超链接将资源关联起来。无状态、统一接口是REST的两种架构约束，超文本驱动是REST的一个关键词，在前面都已经解释过，就不再赘述了。

  从架构风格的抽象高度来看，常见的分布式应用架构风格有三种：

  * 1 分布式对象（Distributed Objects，简称DO）
    架构实例有CORBA/RMI/EJB/DCOM/.NET Remoting等等

  * 2 远程过程调用（Remote Procedure Call，简称RPC）
    架构实例有SOAP/XML-RPC/Hessian/Flash AMF/DWR等等

  * 3 表述性状态转移（Representational State Transfer，简称REST）
    架构实例有HTTP/WebDAV

  DO和RPC这两种架构风格在企业应用中非常普遍，而REST则是Web应用的架构风格，它们之间有非常大的差别。

  * REST与DO的差别在于：

    > REST支持抽象（即建模）的工具是资源，DO支持抽象的工具是对象。在不同的编程语言中，对象的定义有很大差别，所以DO风格的架构通常都是与某种编程语言绑定的。跨语言交互即使能实现，实现起来也会非常复杂。而REST中的资源，则完全中立于开发平台和编程语言，可以使用任何编程语言来实现。

    >  DO中没有统一接口的概念。不同的API，接口设计风格可以完全不同。DO也不支持操作语义对于中间组件的可见性。

    > DO中没有使用超文本，响应的内容中只包含对象本身。REST使用了超文本，可以实现更大粒度的交互，交互的效率比DO更高。

    > REST支持数据流和管道，DO不支持数据流和管道。

    > DO风格通常会带来客户端与服务器端的紧耦合。在三种架构风格之中，DO风格的耦合度是最大的，而REST的风格耦合度是最小的。REST松耦合的源泉来自于统一接口+超文本驱动。

    REST与RPC的差别在于：

    > REST支持抽象的工具是资源，RPC支持抽象的工具是过程。REST风格的架构建模是以名词为核心的，RPC风格的架构建模是以动词为核心的。简单类比一下，REST是面向对象编程，RPC则是面向过程编程。

    > RPC中没有统一接口的概念。不同的API，接口设计风格可以完全不同。RPC也不支持操作语义对于中间组件的可见性。

    > RPC中没有使用超文本，响应的内容中只包含消息本身。REST使用了超文本，可以实现更大粒度的交互，交互的效率比RPC更高。

    > REST支持数据流和管道，RPC不支持数据流和管道。

    > 因为使用了平台中立的消息，RPC风格的耦合度比DO风格要小一些，但是RPC风格也常常会带来客户端与服务器端的紧耦合。支持统一接口+超文本驱动的REST风格，可以达到最小的耦合度。

    比较了三种架构风格之间的差别之后，从面向实用的角度来看，REST架构风格可以为Web开发者带来三方面的利益：

* 简单性
  
  > 采用REST架构风格，对于开发、测试、运维人员来说，都会更简单。可以充分利用大量HTTP服务器端和客户端开发库、Web功能测试/性能测试工具、HTTP缓存、HTTP代理服务器、防火墙。这些开发库和基础设施早已成为了日常用品，不需要什么火箭科技（例如神奇昂贵的应用服务器、中间件）就能解决大多数可伸缩性方面的问题。

* 可伸缩性
  
  > 充分利用好通信链各个位置的HTTP缓存组件，可以带来更好的可伸缩性。其实很多时候，在Web前端做性能优化，产生的效果不亚于仅仅在服务器端做性能优化，但是HTTP协议层面的缓存常常被一些资深的架构师完全忽略掉。

* 松耦合

  > 统一接口+超文本驱动，带来了最大限度的松耦合。允许服务器端和客户端程序在很大范围内，相对独立地进化。对于设计面向企业内网的API来说，松耦合并不是一个很重要的设计关注点。但是对于设计面向互联网的API来说，松耦合变成了一个必选项，不仅在设计时应该关注，而且应该放在最优先位置。



# API的演进

## 版本

   我们常见的API设计有以下三种方式

   * 1. 在URL中放版本的信息: <font color=#c7254e size=7 face="黑体"> Get    www.xxx.com/v1/index/users/1 </font>
   * 2. 自定义的 Accept Header：<font color=#c7254e size=7 face="黑体"> Accept: application/json+v1</font>
   * 3.自定义 <font color=#c7254e size=7 face="黑体">Header：X-Api-Version: 1</font>

# URI规范

## URL的一些注意事项

   * 不用大写；
   * 用中杠-不用下杠_；
   * 参数列表要encode；
   * URI中的名词表示资源集合，使用复数形式。

    资源集合实例:

   ```python
      /zoos                              #所有动物园
      /zoos/1/animals             #id为1的动物园中的所有动物
   ```

   单个资源实例

   ```python
      /zoos/1                     #id为1的动物园
      /zoos/1;2;3               #id为1，2，3的动物园
   ```

##  避免层级过深的URL访问

   过多的URL层级容易导致URL的膨胀和不容易维护，且安全性比较低。譬如  <font color=#c7254e size=7 face="黑体">GET /zoos/1/areas/3/animals/4 </font>，这个时候我们应该 
   > 尽量去使用查询参数代替路径中的实体导航，如GET /animals?zoo=1&area=3；

## 对抽象概念的访问（譬如说一对多资源的访问）
  
   服务端的抽象实体必须通过父类实体的ID去访问（譬如说一的一方的ID）然后才是/抽象实体本身譬如说   <font color=#c7254e size=7 face="黑体"> GET /user/1/addresses</font>
   >  抽象实体并不是单一的一个实体类对象，它的生命周期完全依赖父实体，无法独立存在，在实现上通常是对数据库表中某些列的抽象，不直接对应表，也无id。一个常见的例子是 User — Address，Address是对User表中zipCode/country/city三个字段的简单抽象，无法独立于User存在。必须通过User索引到Address，就跟上面我们写的栗子一样，先通过USER索引到地址然后再是其它关联。

# Request规范

## HTTP方法CRUD
   
   * GET:  查询

   ```python
   
      GET  /user                                              //查全部用户
      GET  /users/1                                         //查详情
      GET  /user/address                                //查这个用户的所有地址
      GET  /users/1/address                           //查单个地址
      
   ```

   * POST:  在创建单个资源的时候

   ```python
   
      POST /role                                              //新增单个角色
      POST /role/1/account                             //为ID为1的角色分配一个账户
  
   ``` 

   * PUT:  更新资源

   ```python
  
      PUT  /user/1
      PUT  /ROLE

   ```

   * DELETE: 删除

   ```python

      DELETE   /users/1/address/2                  //上次ID为1的第2个地址
      DELETE   /users/1/address/2;3;4;5         //删除多个地址
      DELETE   /users/1/address                    //删除ID为1的所有地址
      DELETE  /users/1                                   //删除ID为1的用户

   ```

## 查询参数

  <table>

  <tr><td>&nbsp;&nbsp;&nbsp;术语&nbsp;&nbsp;&nbsp;</td><td>示例&nbsp;&nbsp;&nbsp;</td><td>备注</td></tr>

  <tr><td>&nbsp;&nbsp;&nbsp;过滤条件&nbsp;&nbsp;&nbsp;</td><td>?type=1&age=16&nbsp;&nbsp;&nbsp;</td><td>允许一定的uri冗余，如/zoos/1与/zoos?id=1</td></tr>

  <tr><td>&nbsp;&nbsp;&nbsp;排序&nbsp;&nbsp;&nbsp;</td><td>?sort=age,desc</td><td></td></tr>

  <tr><td>&nbsp;&nbsp;&nbsp;投影&nbsp;&nbsp;&nbsp;</td><td>?whitelist=id,name,email</td><td></tr>

  <tr><td>&nbsp;&nbsp;&nbsp;分页&nbsp;&nbsp;&nbsp;</td><td>?limit=10&offset=3</td><td></td></tr>

  </table>

## 常见的三种body format格式

  *  1.Content-Type: application/json
    
    ```python
       POST /v1/animal HTTP/1.1
       Host: api.example.org
       Accept: application/json
       Content-Type: application/json
       Content-Length: 24

       {   
             "name": "Gir",
             "animalType": "12"
       }
    ```
  * 2.Content-Type: application/x-www-form-urlencoded (浏览器POST表单用的格式)

    ```python
       POST /login HTTP/1.1
       Host: example.com
       Content-Length: 31
       Accept: text/html
       Content-Type: application/x-www-form-urlencoded

       username=root&password=Zion0101
    ```
  * 3.Content-Type: multipart/form-data; boundary=—-RANDOM_jDMUxq4Ot5 (表单有文件上传时的格式)



# Response规范
  * 1.response的body直接就是数据，不要做多余的包装

    ```python
       {
            "result":{"name":123123, "age":22}
       }

    ```

* 2.常用的集中HTTP方法成功处理后的返回格式

  * GET    :             返回一个对象或者集合
  * POST :             返回新增成功的对象，或者受影响的行数（添加个数）
  * PUT/PATCH     返回更新成功后的西乡，或者受影响的行数（编辑个数）
  * DELETE           返回空值，或受影响的函数（删除的个数）





# 参考
> [Roy Thomas Fielding的博士论文《Architectural Styles and the Design of Network-based Software Architectures》](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)

> [理解本真的REST架构](http://www.infoq.com/cn/articles/understanding-restful-style)

> [RESTful API 设计最佳实践](http://blog.jobbole.com/41233/)
