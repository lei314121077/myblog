# beegoAPI开发

## 目录解析 
main.go 是程序的统一入口文件

bapi 是生成的二进制文件

conf 配置文件目录，app.conf

controllers 控制器目录，主要是逻辑的处理

models 是数据处理层的目录

docs 是自动化生成文档的目录

lastupdate.tmp 是一个注解路由的缓存文件

routers是路由目录，主要涉及一些路由规则

swagger 是一个html静态资源目录，是通过bee自动下载的，主要就是展示我们看到的界面及测试

test 目录是针对应用的测试用例，beego相比其他revel框架的好处之一就是无需启动应用就可以执行test case。
