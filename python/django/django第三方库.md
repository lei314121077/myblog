## 核心

   * Django 这个应该不用多说了吧？
   * Django-debug-toolbar 这个有人不知道麼？调式django程序必备，建议关注。
   * Django-model-utils 如果使用类视图的话，这个库提供了很多有用的Field和Mixin，建议关注。
   * Ipdb 断点调试程序，可以说是pdb的加强版。类似于ipython和python的关系。
   * Pillow 一款python的图形处理库，替代PIL的。
   * pip 这个也不多说。
   * Sphinx 为python程序生成文档的。
   * MkDocs 如果喜欢markdown语法，可以用这个替代Sphinx，建议关注。
   * virtualenv以及virtualenvwrapper 这两个不多说。
   
## 异步

   * celery 异步任务队列，建议关注。
   * flower 配合celery使用，用于监控。
   * rq 用于处理后台任务的库，基于redis。
   * django-rq 一个简单的app，配合rq在django使用。
   * django-background-tasks 一个基于数据库的异步任务队列
   
## 数据库

   * django-db-tools 这个本人没用过，看说明是设置数据库为只读模式的？
   * psycopg2 用于操作postgresql数据库，类似于mysql-python。
   * django-redis 链接redis数据库的。

## 部署

   * circus 没用过，作者特意说明这个只有大型程序才有必要使用，命令行程序看进程以及套接字信息的。
   * dj-database-url 没用过，看说明是简化settings中databases配置的。
   * django-heroku-memcacheify 没用过，文档说这个是为了部署在heroku上的程序方便设置memcache的。
   * Fabric 神器，尤其是部署集群的时候，建议关注。
   * Invoke 和fabric类似，支持python3。
   * Supervisor 神器，除了用来部署django程序，可以干很多事情，建议关注。

## 表单

   * django-crispy-forms 让人更简单优雅的控制表单样式。
   * django-foppyforms 和上面的可以搭配使用，完全控制表单样式。
   * django-forms-bootstrap bootstrap样式的表单。
   * django-forms-builder 可以控制admin的表单样式。
   * django-attachments 一款通用的附件上传程序。

##　日志
　　　
   * logutils 加强了原生的logging。
   * Sentry 一个在线记录异常的网站。
   * App Enlight 同上。
   * Newrelic 功能同上，还包含了性能分析等，收费。类似的还有opbeat。

## 项目模板

   * cookiecutter-django 很好很强大，修改了原生的django项目结构，这么做的原因请看书中解释，作者的项目，建议关注。
   * Cookiecutter 上面那个基于这个项目，作者妻子的项目。
   * django-kevin 类似第一个项目，不过生成的是herlku的结构。
   * django-herokuapp 同上。

## REST APIs

   * django-rest-framework 不多说了，不过本人基本不用这个框架，每次都手动开撸自己从头写。
   *　django-jsonview 一个简单的装饰器，把python对象(列表和字典，类实例能不能自动转本人没试过)转换为json格式返回。
   *　django-tastypie 另一个rest框架，没用过，看起来比第一个简单。

## 安全

   * bleach 一个简单的白名单。
   * defusedxml 强制使用xml格式？没用过不多说。
   * django-autoadmin 自动生成admin密码的。
   * django-admin-honeypot 一个假的管理后台登录界面，并记录登录操作。
   * django-axes 同上，记录登录失败行为的。
   * django-ratelimit-backend 登录速度限制，防暴力破解的。
   * django-passwords 检测密码强度的。
   * django-secure 这个比较杂，看文档吧还是。

## 测试
   
   * coverage 这个不多说，建议关注。
   * django-coverage-plugin coverage的django插件，可以用来覆盖测试django的模板，建议关注。
   * django-test-plus 增强了默认的TestCase，建议关注。
   * factory_boy 生成测试数据的库，建议关注。
   * model_mommy 同上。
   * mock 这个已经集成在Python3.4了。
   * pytest python测试工具，建议关注。
   * pytest-django 这是一个基于pytest的django插件，建议关注。
   * pytest-cov 把pytest和coverage结合的插件。
   * pytest-xdist 多进程执行测试。
   * nose 一个单元测试模块。
   * pytest-sugar 增强了pytest的提示等。
   * tox 提供了一个命令行工具自动打包、测试、发布程序，建议关注。

## 用户注册

　　* django-allauth 提供了常见的注册和认证方式，比如邮件、twitter、facebook、github、google等。社交支持在我大天朝比较鸡肋。
　　* python-social-auth 同上。
　　* django-authtools 自定义用户模型。

## 视图
   
   * django-braces 如果你使用类视图，强烈建议使用这个库，提供了很多有用的mixin类,建议关注。
   * django-extra-views 提供了很多通用类视图，建议关注。
   * django-vanilla-views 这个替换了django提供的通用类视图，使代码更精简，建议关注。

## 时间

   * python-dateutil 扩展了python自带的datetime模块。
   * pytz 如果你被时区坑过，建议使用这个库。

## 其他
   
   * awesome-slugify 这个库有点意思，表面看处理字符串的，但实际上是处理url的。
   * unicode-slugify 这个和第一个库类似。
   * django-autoslug 这个和第一个库类似。
   * dj-stripe stripe是一个国外支付平台，天朝内没大用。
   * django-compressor 用于压缩css和js。
   * django-extensions 包括management命令扩展,数据库字段扩展,admin后台扩展等，建议关注。
   * django-haystack 提供统一的 API 允许你使用不同的搜索后端，包括 Solr, Elasticsearch, Whoosh, Xapian 等等。
   * django-pipeline 压缩css和js，使用cssmin和jsmin包。
   * django-htmlmin 压缩html代码的。
   * django-reversion 类似版本控制，可以记录每次数据变化的情况，以及回滚，建议关注。
   * django-environ 简化settings配置的，建议关注。
   * django-watson 跨表全文检索的，建议关注。
   * django-storages-redux 用来存储图片、文件到不同后端的，比如亚马逊s3或者微软的azure。
   * envdir 和虚拟环境有关，没用过不多说。
   * flake8 代码格式化的。
   * pathlib 这个挺有意思，使用面向对象的方法来处理系统路径。
   * pip-tools 一个pip命令的扩展。 
   * pyyaml 处理yaml格式数据。
   * requests 神器，用了这个我再也没用过urllib2库了，建议关注。
   * silk 一个在线django性能检查调优工具，建议关注。
   * Unipath 和12类似，面向对象的方式处理路径。
   * whitenoise 管理静态文件的,建议关注。
   * pandoc 提供了多种文档格式转换，比如markdown to rst等，建议关注。
   
   
   
