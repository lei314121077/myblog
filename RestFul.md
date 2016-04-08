# REST简介
> REST是设计风格而不是标准。REST通常基于使用HTTP，URI，和XML以及HTML这些现有的广泛流行的协议和标准。
* 资源是由路由也就是URI来指定的。
* 对资源的操作包括获取、创建、修改和删除资源，这些操作正好对应HTTP协议提供的GET、POST、PUT和DELETE方法。
* 通过操作资源的表现形式来操作资源。
* 资源的表现形式则是XML或者HTML，取决于读者是机器还是人，是消费web服务的客户软件还是web浏览器。当然也可以是任何其他的格式。

# REST约束
REST架构风格最重要的架构约束有6个
  *客户-服务器（Client-Server）
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















# 参考
> [Roy Thomas Fielding的博士论文《Architectural Styles and the Design of Network-based Software Architectures》](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)

> [理解本真的REST架构](http://www.infoq.com/cn/articles/understanding-restful-style)

