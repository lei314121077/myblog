
# 目录

* [安装](#安装)
* [Django自带命令行](#Django自带命令行)
* [jango项目和模块结构](#jango项目和模块结构)

#  安装
	
* pip安装
	
	* Ubuntu:

		```python
			sudo apt-get install python-pip

		```
	* centos

		```python

			yum install python-pip

		```

	* mac os x

		```python
			brew install pip
		```

	* 升级

		```python
			sudo pip install --upgrade pip
		```

	> 或者直接用[get-pip])(https://pip.pypa.io/en/latest/installing/)来安装

* 用pip来安装Django

	* 安装

		```python
			sudo pip install Django

			# 或者
			sudo pip install Django==1.8.6
			sudo pip install Django==1.10.3
		```

# Django自带命令行
	
	Django 自带的命令行可直接在当前系统下的Shell（Terminal）终端上运行

	* 新建一个Django项目

		```python

			django-admin.py startproject 项目名

		```
	
	* 新建一个App 项目模块

		进入到当前项目下，有一个Manage.py的文件

		```python

			python manage.py startapp app模块名

			或 django-admin.py startapp app-name

		```

	* 同步你的数据库

		使用这个命令可以自动创建数据库表，前提是你的Models.py必须新增勒模型对象（类），而不用苦逼的自动去数据库写SQL语句创建，这个就是Django的ORM的好处，如果你对Models做了修改django1.7之前的版本是无法自动更改表的结构的，你可以[参考](http://www.ziqiangxuetang.com/django/django-data-migration.html)

		```python
			
			python manage.py syncdb

			# Django 1.7.1及以上的版本需要用以下命令
			
			python manage.py makemigrations
			python manage.py migrate

		```

	* 运行或使用开发服务器

		开发服务器，即开发时使用，一般修改代码后会自动重启，方便调试和开发，但是由于性能问题，建议只用来测试，不要用在生产环境。

		```python

			python manage.py runserver
 
			# 当提示端口被占用的时候，可以用其它端口：
			python manage.py runserver 8001
			python manage.py runserver 9999
			（当然也可以kill掉占用端口的进程）
			 
			# 监听所有可用 ip （电脑可能有一个或多个内网ip，一个或多个外网ip，即有多个ip地址）

			python manage.py runserver 0.0.0.0:8000

			# 如果是外网或者局域网电脑上可以用其它电脑查看开发服务器
			# 访问对应的 ip加端口，比如 http://172.16.20.2:8000

		```

	* 清空数据库

		此命令会询问是 yes 还是 no, 选择 yes 会把数据全部清空掉，只留下空表
	
		```python

			python manage.py flush
		
		```
	* 创建超级管理员

		```python

			python manage.py createsuperuser
			# 按照提示输入用户名和对应的密码就好了邮箱可以留空，用户名和密码必填
 
			# 修改 用户密码可以用：
			python manage.py changepassword username
		
		```

	* [导出数据](http://www.ziqiangxuetang.com/django/django-data-migration.html) [导入数据](http://www.ziqiangxuetang.com/django/django-import-data.html)

		```python

			python manage.py dumpdata appname > appname.json
			python manage.py loaddata appname.json
		
		```
	* Django 项目环境终端

		如果你安装了 bpython 或 ipython 会自动用它们的界面，推荐安装 bpython。<br>
		这个命令和 直接运行 python 或 bpython 进入 shell 的区别是：你可以在这个 shell 里面调用当前项目的 models.py 中的 API，对于操作数据，还有一些小测试非常方便。

		```python

			python manage.py shell

		```

	* 数据库命令行

		Django 会自动进入在settings.py中设置的数据库，如果是 MySQL 或 postgreSQL,会要求输入数据库用户密码。

		在这个终端可以执行数据库的SQL语句。如果您对SQL比较熟悉，可能喜欢这种方式。

		```python
			python manage.py dbshell
		```

	* 更多的命令

		> python manage.py 可以看到详细的列表，在忘记子名称的时候特别有用。


# django项目和模块结构

	* [urls.py](http://www.ziqiangxuetang.com/django/django-views-urls.html)
		
		网址入口，关联到对应的views.py中的一个函数（或者generic类），访问网址就对应一个函数。

	* [views.py](http://www.ziqiangxuetang.com/django/django-views-urls.html)

		处理用户发出的请求，从urls.py中对应过来, 通过渲染templates中的网页可以将显示内容，比如登陆后的用户名，用户请求的数据，输出到网页。

	* [models.py](http://www.ziqiangxuetang.com/django/django-models.html)

		与数据库操作相关，存入或读取数据时用到这个，当然用不到数据库的时候 你可以不使用。

	* [forms.py](http://www.ziqiangxuetang.com/django/django-forms.html)

		表单，用户在浏览器上输入数据提交，对数据的验证工作以及输入框的生成等工作，当然你也可以不使用。

	* [templates 文件夹](http://www.ziqiangxuetang.com/django/django-template.html)

		views.py 中的函数渲染templates中的Html模板，得到动态内容的网页，当然可以用缓存来提高速度。

	* [admin.py](http://www.ziqiangxuetang.com/django/django-admin.html)
		
		后台，可以用很少量的代码就拥有一个强大的后台。

	* [settings.py](http://www.ziqiangxuetang.com/django/django-settings.html)

		Django 的设置，配置文件，比如 DEBUG 的开关，静态文件的位置等。




# 参考
	
	[教程](http://www.ziqiangxuetang.com/django/django-views-urls.html)





































