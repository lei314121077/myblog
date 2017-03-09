
# 模块开发
 * [10开发文档](https://www.odoo.com/documentation/10.0/howtos/backend.html)
 * [9.0开发文档](https://www.odoo.com/documentation/9.0/howtos/backend.html#build-an-odoo-module)
 * [8.0开发文档](http://blog.sunansheng.com/python/odoo/odoo.html#sec-3)
 
## 一些常用的依赖包
  ```python
  pip install http://download.gna.org/pychart/PyChart-1.39.tar.gz
  pip install babel
  pip install docutils
  pip install feedparser
  pip install gdata
  pip install Jinja2
  pip install mako
  pip install mock
  pip install psutil
  pip install psycopg2
  pip install pydot
  pip install python-dateutil
  pip install python-openid
  pip install pytz
  pip install pywebdav
  pip install pyyaml
  pip install reportlab
  pip install simplejson
  pip install unittest2
  pip install vatnumber
  pip install vobject
  pip install werkzeug
  pip install xlwt
  pip install pyopenssl
  pip install lxml
  pip install python-ldap
  pip install pillow
  pip install decorator
  pip install requests
  pip install pyPdf
  pip install wkhtmltopdf
  pip install passlib
  ```
## 常用的一些命令
  * 启动 odoo
  
  ```
   sudo start odoo
  ```
  
  * 重启 odoo
  
  ```
    sudo restart odoo
  ```
  * 停止 odoo
  
  ```
   sudo stop odoo
  ```
  
  * 重启 nginx
    
    ```
      sudo /etc/init.d/nginx reload
    ```
    
  * 重启[Postgresql数据库](http://cdwanze.github.io/%E7%94%B5%E8%84%91/python/%E6%95%B0%E6%8D%AE%E5%BA%93/postgresql%E5%9F%BA%E7%A1%80.html)
  
  ```
    sudo service postgresql restart
  ```
## [OERP零散](https://www.odoo.com/zh_CN/page/tour)
  
* 替换logo为自己公司的logo
    
    通常方法：
    
    1. 登录系统后，把鼠标放到左上角LOGO位置，点击出现的‘编辑公司数据’
    2. ​在出现的页面的LOGO位置，点击编辑按钮，更换LOGO
    3. ​刷新页面，如果没看到新LOGO，则点击导航栏的‘网站’功能，进入编辑网站模式
    4. 点击导航栏右方‘定制’，不勾选‘Show Logo’​，然后再勾选‘ShowLogo’即可

    最直接暴力的方法:

    ```
      1、用你自己的logo替换/opt/odoo/addons/web/static/src/img/下面的logo.png（登录后左上角logo）和logo2.png（用于数据库选择页面）。
      2、更改POS的logo：替换/opt/odoo/addons/point_of_sale/static/src/img/logo.png
      
      # 进到目录
        
        $ cd ./openerp/addons/base/static/img
      
      # 替换名称为 logo_white.png 的logo图片
        
        $ sudo vm ./openerp/addons/base/static/img/logo_white.png   logo_white.png   
    
    ```
    
    > 更换完，如果加载之后还是原来的logo那么，请关闭你的浏览器然后再清一下缓存。
    
  * 修改版权声明 Powered by Odoo
   ```
    # 修改版权声明有3个地方1、database manage页面，2、login 页面,3、后台左侧菜单栏底部
    第一步: 
    修改这个文件下的 odoo/addons/web/views/webclient_templates.xml “<div class="oe_footer">”把它修改成你自己的或者直接注释掉
    <!--div class="oe_footer">
    Powered by <a href="http://www.openerp.com" target="_blank"><span>Odoo</span></a>
    </div-->
    第二步：
    # 编辑/odoo/addons/web/static/src/css/base.css下的
    .openerp .oe_leftbar > div .oe_footer{
    .openerp .oe_leftbar > div .oe_footer a{
    .openerp .oe_leftbar > div .oe_footer a span {
    我是直接隐藏掉，即新增dispay：none；
   ```
  或者你可以[参考这里](http://odoo.guide/debranding-odoo-backend/)
  
## [定制开发](http://blog.sunansheng.com/python/odoo/odoo.html#sec-3)
  
  * 快速创建自己的模块(./odoo.py scaffold 我的模块名  模块包容器)
  
  ```python
     $  ./odoo.py scaffold  mymodule myaddons
     #  通常情况下我们要在addons下面创建自己的定制模块mydodule
     # 姿势是这样
     $  ./odoo.py scaffold  mymodule addons
  ```
  * 模块文件夹清单
  
    然后作为Odoo框架的模块还必须新建一个 [__openerp__.py](http://www.oejia.net/blog/2016/04/22/odoo_config.html) 文件，最小型的什么都不做的Odoo模块就需要这两个文件，一个是这个 __openerp__.py 文件，一个是 __init__.py 文件。
    
    * data文件夹 ，放着demo和data xml
    
    * models文件夹，放着模型定义
    
    * controllers文件夹，http路径控制
    
    * views文件夹，网页视图和模板
    
    * static文件夹，网页的一些资源，里面还有子文件夹:css，js，img，lib等等。
    
    scaffold自动创建的 __openerp__.py 文件大致内容如下:
    ```python
      # -*- coding: utf-8 -*-
      {
          # 模块名称
          'name': "testModule",
          # 模块简介
          'summary': """my first Module test test test!""",
          # 模块描述
          'description': """
              Long description of module's purpose
          """,
          # 模块作者
          'author': "raymond",
          # 模块网址
          'website': "http://www.dconline.com",

          # Categories can be used to filter modules in modules listing
          # Check https://github.com/odoo/odoo/blob/master/openerp/addons/base/module/module_data.xml
          # for the full list
          # 模块分类
          'category': 'test',
          # 版本号
          'version': '0.1',

          #版权信息,默认是AGPL-3
          'license': 'AGPL-3',
          # any module necessary for this one to work correctly

          #本模块的依赖关系，这里主要是指本模块对于Odoo框架内其他的模块的依赖。如果本模块实在没什么依赖，就把 base 模块填上去。
          'depends': ['website'],

          # always loaded
          # 模块必加载的数据文件：本模块要加载的数据文件，别看是数据文件，似乎不怎么重要，其实Odoo里面视图，动作，工作流，模型具体对象等等几乎大部           分内容都是通过数据文件定义的。
          'data': [
              # 'security/ir.model.access.csv',
              'views/views.xml',
              'views/templates.xml',
          ],
          # only loaded in demonstration mode
          #demonstration下才加载的数据文件：这里定义的数据文件正常情况下不会加载，只有在demonstration模式下才会加载，具体就是你新建某个数据库           是勾选上了加载演示数据那个选项。
          'demo': [
              'demo/demo.xml',
          ],
          #默认True，可设为False禁用该模块
          'installable': True,
          #默认False，如果设为True，则这个模块成为一个应用了。你的主要模块建议设置为True，这样进入Odoo后点击本地模块，然后默认的搜索过滤就是 应           用 ，这样你的主模块会显示出来。
          'application': True,
          #默认False，如果设为True，则根据其依赖模块，如果依赖模块都安装了，那么这个模块将自动安装，这种模块通常作为胶合(glue)模块。
          'auto_install': False,

      }
    ```

## [仓储模块](https://www.odoo.com/zh_CN/page/tour)

## [财务模块](https://www.odoo.com/zh_CN/page/tour)

## [车辆管理](https://www.odoo.com/zh_CN/page/tour)

