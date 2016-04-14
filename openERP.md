# OpenERP应用系统架构
  OpenERP （数据库服务器） ------M
  
  > OpenERP采用开源数据库服务器，PostgreSQL database server。在 OpenERP 中,用户界面不是通过 HTML 或其他程序代码生成,而是直接存放
  在数据库中。运行时直接从数据库中取出数据,然后渲成需要的界面，也就是我们长说的View视图。
  
  OpenERP （应用服务器） ------C
  > 应用服务包含所有的业务逻辑代码。以及简单的CRUD, 即新增Create、获取Retrieve、更新Update、删除Delete操作，和复杂的条件过滤与查
  询。
  
  OpenERP-Client（图形界面客户端）------V

  * GUI-Client
    > OpenERP 的客户端不含任何业务逻辑代码,也不 包含任何界面代码,即所谓的“瘦客户端”。OpenERP 的 Client 的功能是,通过调用 OpenERP应用
    服务器的各种对象的方法,调用或从数据库中取得界面所需的数据(XML 格式定义的界面),以及业务数据,合并二者,渲染成用户界面,在屏幕上显示出来。
  
  * Web-Client
    > OpenERP网页形式的客户端，不同的是它把来自数据库的界面和业务数据渲染成HTML格式的网页形式，因此我们可以通过网页浏览器去访问，譬如说Google的Chrome，Micorft的IE还有Firefox等浏览器访问。
  
# OpenERP 应用服务器架构
  <p>
   OpenERP之所以闻名是除了它是国际开源的ERP系统外，另一个很受广大开发者欢迎的特性就是它的灵活的模块化设计。它整个应用服务器都是有松散的模块构成，模块间的耦合度非常低。而怎样做到松散耦合是我们在软件开发以及软件设计当的一个非常困难的问题，而OpenERP在这点上是目前为止所有ERP软件中做得最好的。
  </p>
  
  OpenERP的应用服务架构最主要由以下几部分构成
  
  * ORM
  > Object Relation Mapping，负责数据对象到数据库的访问。在 OpenERP 的业务对象中，你不必
写一行数据库访问代码，就自动具备 CRUD 的数据库访问功能。
  
  * BMD
  > Base Module Distribution，是一个基础模块，必不可少。其他模块，你可以自己任意添加，开
源社区有超过 500 个以上的可用模块。
  
  * Report Engine，负责生成各种报表。
  > 目前支持的报表格式有 PDF，OpenOffice，HTML 三种。
  
  * Workflow Engine，工作流引擎。
  > 支持任意复杂度的工作流，OE 的工作流使用 XML 格式文件定义，
目前也ᨀ供简单的图形化工作流编辑工具。

  * WebService，供网络调用接口。
  > 目前支持 Net-RPC、XML-RPC 两种

 
