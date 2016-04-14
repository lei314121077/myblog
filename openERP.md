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

# OpenERP功能和应用简介

一、 OpenERP的功能模块
    
      *OpenERP*里面的功能模块有很多，我们可以在[OpenERP的官网](https://www.odoo.com/)直接看到，据说现在连APP都已经有了，2013年的时候我们开发的还只是全部都是网页端的，不瞎逼逼了，让我们来看看部分的功能模块吧。
      
      Enterprise Modules Management (企业管理模块)
        *   Sales  (销售)
        *   Purchase (购买)
        *   Services Management （服务管理）
        *   Invoicing （发票管理）
        *   Point of Sales （POS机）
      
      Logistics(物料管理模块)
        *   Warehouse Management （仓库or仓储）
        *   Shipping Management   （运算or航运）
        *   Manufacturing         （生产）
        *   Quality & Repairs     （质量与维修）
        *   Products and pricelists （产品与价格）
        
      Accounting & Finance(财务管理)
        * Accounting （会计）
        * Analytic Accounting （会计分析）
        * Budgets （预算）
        * Payments Management （支付管理）
        * Asset Management  （资产管理）
        * Bank interfaces   （银行接口）
        
      Human Resources(人力资源管理) 
        * Expenses  （支出or费用）
        * Skills Management （技能管理or培训）
        * Holidays  （假期管理）
        * Attendances  （考勤管理）
      
      CRM & SRM (客户和供应商关系管理) 
        * Customer Relationship Mgt   （客户关系管理）
        * Mail Gateway  （邮件网关）
        * Portals   （门户网站）
        * Direct Marketing  （市场直销）
        * Phone Calls （通讯录）
        
      Project Management(项目管理) 
        * Operational Management
        * Financial Management
        * Timesheets
        
      Daily Productivity(日常工作管理) 
        * Integrated DMS
        * Outlook/Thunderbird 
        * Getting Things Done 
        * Calendars
        
      Efficient Communication(沟通工具) 
        * Wiki
        * Webmail
        * Dashboards
        * Alerts
        
      Business Process Management(业务流程管理) 
        * End-User Processes
        * Workflow Engine
        
      Association Management 
        * Membership
        * Events Organization 
        * Fund Raising
      
      IT Companies(IT 公司管理工具) 
        * Bug Tracker
        * Scrum Methodology
        
      Fully Customizable(灵活的定制化功能) 
        * Report Designer
        * View Editor
        * Workflow Editor
        * Configurable Actions
      
      Ergonomy
        * Web & Application Interfaces 
        * Gantt & Calendars
        * Dynamic Graphs
        * Integrated Documentation
      
      Flexible
        * Modules System
        * Web-Services
      
      eCommerce
        * Integrated eCommerce 
        * EDI Business Intelligence 
        * Olap Database 
        * Cube Designer
        * Data Browser
        
      Miscelleanous Tools 
        * Networks
        * Ideas 
        * Lunch 
        * Voip

# OpenERP开发简介
  
  > OpenERP采用Python代码实现，OpenERP的功能开发遵循彻底的MVC模式，也就是我们开发中常用到的Model、View、Controller。
  
  * Model 用户数据模型开发
  
  > 在 OpenERP 中,简单的对象, 你只要定义对象的各个字段,系统会自动为你创建数据库表,自动生成 CRUD 的数据库操作代码。因此,你不必另外在数据库中创建 Table,也不必写 Insert、Select、Delete、Update 等数据库操作 代码,这些都留给 OpenERP 帮你去搞定。
  
    ```python
      class qingjia_qingjd(osv.osv):
        _name = 'qingjia.qingjd'
        _description = '请假单' 
        _columns = {
          'shenqr': fields.many2one('hr.employee', '申请人', required=True), 
          'tians': fields.float('请假天数', required=True),
          'kaisrq': fields.date('开始日期', required=True),
          'shiyou': fields.text('请假事由'),
          'active': fields.boolean('有效'),
          'state': fields.selection([('draft','草稿'),('wait_prove','待批'),('proved','已批'),('rejected','被拒')], '状态', required=True)} 
      qingjia_qingjd()
    ```
  
  * View 用户界面开发
  
  > OpenERP 中,用户界面的开发不要写任何代码。它是用 XML 格式定义用户界面。

    ```python
      <record model="ir.ui.view" id="view_qingjd_tree"> 
        <field name="name">请假单</field>
        <field name="model">qingjia.qingjd</field>
        <field name="type">tree</field>
        <field name="arch" type="xml">
          <tree string="请假单">
            <field name="shenqr" select="1"/>
            <field name="tians" />
            <field name="kaisrq" select="1"/> 
            <field name="shiyou" />
            <field name="state" select="1"/>
          </tree> 
        </field>
      </record>
      <!-- 表单视图 代码从略 -->
  ```
  
  * Action (Controller) 控制器开发
  
  > Action也就是我们要讲的触发菜单的开发,在 OpenERP 中,叫做 Action,也就是 MVC 中的 C,Controller。OpenERP 的 Action 也不用写代码,是用 XML 定义的。




 
