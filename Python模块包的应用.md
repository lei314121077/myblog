# Virtualenv（虚拟环境）
  
  > virtualenv通过创建独立Python开发环境, 来解决项目之间环境的依赖以及版本之间内存在的间接权限类的问题。
  
  * 安装
  
    ```python
      $ pip install virtualenv
      $ sudo pip install virtualenv
      $ easy_install virtualenv
    ```
  
  * 正确的姿势 (基本使用)
  
    创建一个名为odoo_test的目录, 假设你已经安装了odoo_test/bin/python, 然后创建了lib,includelib,include,bin目录,安装了pip
    ```python
      $ virtualenv odoo_test 
      
    ```
      1、lib, 所有安装的python库都会放在这个目录中的lib/pythonx.x/site-packages/下
      2 、bin, bin/python是在当前环境是使用的python解释器
      > 如果我们在命令行中运行virtualenv --system-site-packages odoo_test, 会继承/usr/lib/python2.7/site-packages下的所有库, 而最新版本virtualenv把把访问全局site-packages作为默认的行为
  
  * 觉醒（激活）
  
    激活当前virtualenv
    ```python
       $ source ./bin/activate  
    ```
  
  * 闭关 （关闭）
  
    输入下面的命令后就会退出虚拟环境
    ```python
      $ deactivate
    ```
  * 指定目标版本
  
    创建目标版本为2.7的Pyton虚拟环境 
    ```python
      $ virtualenv -p /usr/bin/python2.7 ENV2.7
    ```
  
    创建目标版本为3.4的python虚拟环境
    ```python
      $ virtualenv -p /usr/local/bin/python3.4 ENV3.4
    ```
    
  * 生成可打包的环境
  
    某些特殊需求下,可能没有网络, 我们期望直接打包一个ENV, 可以解压后直接使用, 这时候可以使用virtualenv -relocatable指令将ENV修改为可更改位置的ENV

    ```python
      # 对当前已经创建的虚拟环境更改为可迁移
      ➜ ENV3.4 git:(master) ✗ virtualenv --relocatable ./
      Making script ./bin/easy_install relative
      Making script ./bin/easy_install-3.4 relative
      Making script ./bin/pip relative
      Making script ./bin/pip3 relative
      Making script ./bin/pip3.4 relative
    ```

  * 帮助
  
    ```python
      $ virtualenv -h
    ```
  [Virtualenv官网文档](http://virtualenv.readthedocs.org/)
  
# pip 

  * 下载

  ```
    # wget "https://pypi.python.org/packages/source/p/pip/pip-1.5.4.tar.gz#md5=834b2904f92d46aaa333267fb1c922bb" --no-check-certificate
  ```
  
  * 安装
    
    ```
      # tar -xzvf pip-1.5.4.tar.gz
      # cd pip-1.5.4
      # python setup.py install
    ```
    
  * 正确的姿势
    

    查看已安装的Python模块包以及版本号列表
    ```
      pip list
    ```
    
    安装包
    ```
      pip install *package-name*
    ```
    
    移除包
    ```
      pip uninstall *package-name*
    ```  
    更新包
    ```
      pip install -U *package-name*  
    ```
    包升级
    ```
      pip install --upgrade *package-name*  
    ```
    查看待更新的包
    ```
      pip list --outdate
    ```
    帮助
    ```
      # pip --help
    ```
    
    ```python
    Usage:   
        pip <command> [options]
       
    Commands:
        install                     安装包.
        uninstall                   卸载包.
        freeze                      按着一定格式输出已安装包列表
        list                        列出已安装包.
        show                        显示包详细信息.
        search                      搜索包，类似yum里的search.
        wheel                       Build wheels from your requirements.
        zip                         不推荐. Zip individual packages.
        unzip                       不推荐. Unzip individual packages.
        bundle                      不推荐. Create pybundles.
        help                        当前帮助.
       
      General Options:
        -h, --help                  显示帮助.
        -v, --verbose               更多的输出，最多可以使用3次
        -V, --version               现实版本信息然后退出.
        -q, --quiet                 最少的输出.
        --log-file <path>           覆盖的方式记录verbose错误日志，默认文件：/root/.pip/pip.log
        --log <path>                不覆盖记录verbose输出的日志.
        --proxy <proxy>             Specify a proxy in the form [user:passwd@]proxy.server:port.
        --timeout <sec>             连接超时时间 (默认15秒).
        --exists-action <action>    Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup.
        --cert <path>               证书. 
    ```
    
    [pip官方文档](https://pip.pypa.io/en/latest/installing/)
    
# Requests ()


# 
