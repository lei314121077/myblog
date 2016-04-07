# OpenERP应用系统架构
##数据库服务器 ------M
  OpenERP采用开源数据库服务器，PostgreSQL database server。在 OpenERP 中,用户界面不是通过 HTML 或其他程序代码生成,而是直接存放
  在数据库中。运行时直接从数据库中取出数据,然后渲成需要的界面，也就是我们长说的View视图。
  
##OpenERP应用服务器 ------C
  应用服务包含所有的业务逻辑代码。以及简单的CRUD, 即新增Create、获取Retrieve、更新Update、删除Delete操作，和复杂的条件过滤与查
  询。
  
##OpenERP-Client（图形界面客户端）------V

###GUI-Client
  OpenERP 的客户端不含任何业务逻辑代码,也不 包含任何界面代码,即所谓的“瘦客户端”。OpenERP 的 Client 的功能是,通过调用 OpenERP应用
  服务器的各种对象的方法,调用或从数据库中取得界面所需的数据(XML 格式定义的界面),以及业务数据,合并二者,渲染成用户界面,在屏幕上显
  示出来。
  
###Web-Client
  OpenERP网页形式的客户端，不同的是它把来自数据库的界面和业务数据渲染成HTML格式的网页形式，因此我们可以通过网页浏览器去访问，譬如
  说Google的Chrome，Micorft的IE还有Firefox等浏览器访问。
  
  
