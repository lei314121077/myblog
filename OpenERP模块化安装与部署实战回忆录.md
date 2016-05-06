#  为什么选择OpenERP以及OpenERP的商业价值
> ERP 软件很多,OpenERP 有什么优势呢。四个字概括,价廉物美。

1 首先,OpenERP 是开源软件。ERP 软件实施的成本构成中,
  * 业务及需求分析:0 – 10%
  * 软件授权(License):20 – 30%
  * 系统集成:50% -- 70%
  * 其他:10%
其中,系统集成包括,系统配置,基础数据设置,二次开发,数据恢复,用户培训等。

OpenERP 是开源软件,您可以任意下载源代码,任意修改,不需要授权费。和商业软件相比,您立即
节省 20—30%的费用。

2 其次,OpenERP 的系统集成成本是所有 ERP 软件中最低的。

  * 一是,基于OpenERP部署系统就像搭积木一样简单。

  > OpenERP的模块化是公认最灵活、耦合度最低的。每个功能都是一个独立模块,你可以像搭积木一样,根据功能需要,逐步增加模块。

  * 二是,OpenERP二次开发效率最高。

  > 这得益于OpenERP是用Python语言开发的。OpenERP是世界上唯一一款用Python开发的ERP软件。
据测算,Python 语言的开发效率是 Java 语言的 5—10 倍。也就是同样的二次开发的要求,OpenERP只需要基于Java的ERP软件的1/5甚至1/10 的开发时间。因此,在 ERP 实施的系统集成阶段,您又可以节约一大笔资金。

  * 第三,丰富的功能模块。

  > OpenERP 有超过 500个功能模块,涵盖企业管理中的各个方面,涉及各个行业。而且,这些模块都是开源的,您可以任意使用、修改。在全球超过 1000 位开发人员的参与下,模块数还在不断增加中。

  * 第四,全球各行业的案例证明,OpenERP 是稳定的。

  > OpenERP 从 2002 年开始,历经 8 年发展,有报导的客户遍及全球 20 多个国家。大的客户有法国国家行政学校,有 1500 个用户。法国邮政,卢森堡银行,美国最大的白色家电公司惠而浦等。有报导的行业有,金融保险、生产制造、食品、服务业、教育、娱乐、
书店、在线拍卖等。

注:关于 [Python和Java开发效率的详细对比,您可以查看这里:](http://www.developertutorials.com/tutorials/python/python-and-java-a-side-by-side-comparison-8-01-13/page1.html)

# 下载
 首先要熟悉OpenERP必须先它的源码下下来，然后再进行安装，整个安装过程大概需要半个小时左右。
 


# 安装

#  配置
## 目前OpenERP的界面汉化存在多个版本,一个是官方的5.07版的汉化,一个是[HornERP](http://code.google.com/p/hornerp/)对5.06版的汉化。两个版本术语不尽一致,且两个版本都存在一些翻译欠准确的术语，所以想要更具体一点的双语就需要自己动手去调整或者配置了。

可用的参考
 * [参考1](http://www.3e3c.com/erp/odoo/224.html)
 * [参考2](http://kloud51.com/knowledgebase/185/Install-Odoo-9-ERP-on-Ubuntu-1404.html)
 * [参考3](http://openies.com/install-openerp-odoo-9-on-ubuntu-server-14-04-lts/)
 * [参考4](https://doc.odoo.com/7.0/zh_CN/book/1/1_1_Inst_Config/1_1_Inst_Config_install/)

# 部署

# 异常处理
* [Errno 98] Address already in use
  ```
   $ ps -ef
   $ ps -ef | grep openerp-server
   
   #查看对应的python端口
   $ ps -ef | grep openerp-server
   
   pc       6399  2391  0 14:06 pts/1    00:00:02 python ./openerp-server
   pc       7488  2391  0 14:39 pts/1    00:00:00 grep --color=auto openerp-server
   
   # kill掉然后重新启动
   $ sudo kill -9 -6399 
   
   $ sudo ./openerp-server
 ```
* role "root" does not exist  角色不存在
  ```
   sudo su - postgres -c "createuser -s root"
  ```
*  不存在-某某包异常
 ```
  #方法1
  $ sudo pip install package
  #方法2
  $ sudo apt-get instal python-package
 ```

# PostgresSQL

  * 乱七八糟
      1，安装命令：sudo apt-get install postgresql
      2，安装完后，切换到postgres用户：sudo su postgres
      3，创建新的用户账户：createuser oe
      4，进入数据库：psql template1
      5，修改用户密码：alter role oe with password '123456';      //注意不要忘了分号
      6，退出数据库编辑：\q
      7，打开数据库配置文件：sudo nano /etc/postgresql/9.1/main/postgresql.conf
      8，修改连接权限：#listen_addresses = ‘localhost’改为 listen_addresses = ‘*’
      9，启用密码验证：#password_encryption = on改为password_encryption = on
      10，打开pg_hba.conf：sudo nano /etc/postgresql/9.1/main/pg_hba.conf
      11，在末尾加上可访问ip段：host all all 0.0.0.0 0.0.0.0 md5
      12，重启数据库服务：sudo /etc/init.d/postgresql restart
[参考](http://www.3e3c.com/erp/odoo/119.html)      
说明：在进行数据库配置的时候一定注意连接权限和密码验证的修改，不修改的话是不能进行远程连接的。你可以用pgAdminIII或者一些数据库连接工具进行连接测试，能连接上说明配置成功。




