这里列出一些我这段时间了解的一些golang这门语言的WebFramework的一些了解的概述，不是特别详细，但是后面会慢慢补充吧。
这里列出一些比较常用的或者我自己目前了解到的比较叼的一些框架的特性。

# golang之框架篇

* Beego
  
  目前最喜欢的框架之一，国产的框架，设计灵感来自于 tornado、sinatra 和 flask 这三个框架，但是结合了 Go 本身的一些特性（interface、struct 嵌入等）而设计的一个框架。
  > 支持MVC、REST、智能路由、日志调试、配置管理、模板自动渲染、layout设计、中间件插入逻辑、方便的JSON/XML服务、强大的Bee工具，
  > 让你在开发的过程当中更加如鱼得水，且bee支持web框架、API框架、游戏框架等等，目前国内很多大公司都在用，包括盛大、360、腾讯、阿里、YY这些巨头。
  你可以在这里查看[beego的相关源码](https://github.com/astaxie/beego)方便你更好的了解它。
  
* GoRestful

* Gin

  gin 和 echo。这两个框架，在同类中，路由性能最高，超出其他框架一大截，如果从企业的角度去考虑做技术架构的选型那么我建议你选择Gin
  
  * 选择原因
    * gin拥有比较详细的出错信息，极为方便调试。
    * 非常适合团队开发，这个很重要。
    * 强大的路由性能，gin目前是所有web框架中，路由性能最好的。
  
  > gin的主创是2个大学生。每年寒暑假就频繁更新，快到期末考试了，就完全不更新了。两人不在的时候，有网友在帮忙热情的维护，但主要是修bug、整理中间件。
  > 框架本身的发展，还是靠主创寒暑假爆发。就是这样的框架，连csico都在用。。。好在，gin的代码注释量大，易读性高，便于其他人参与。
  > 而且包装中间件，也超级容易。
  > 作者本人的态度是，对于一个在github上，start达到5000+的项目，他怎么可能会不去维护。请大家放心使用，到寒暑假了，他自然会去更新。。。

* Echo


* Martini
* Revel

