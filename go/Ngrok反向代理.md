# [Ngrok官网](https://ngrok.com/)

   Ngrok服务的核心功能是能够将你本机的HTTP服务（站点）或TCP服务，通过部署有ngrok服务的外网伺服器暴露给外网访问！在国内开发微信公众号、企业号以及做前端开发的朋友想必对ngrok都不陌生吧，就目前来看，ngrok可是最佳的在内网调试微信服务的tunnel工具，同时ngrok以及服务端的ngrokd都是开源的，你可以去[github](https://github.com/inconshreveable/ngrok)上了解其源码结构。
   
## 用法 

   * 安装
   
   ```go
        # mac install 
        $ brew install ngrok
        # 认证
        $ ngrok authtoken <your-token>
        # run
        $ ngrok http 8080
        # 然后等链接到服务器会获得ngrok的地址
   ```
      
## 参考

   * [搭建自己的ngrok服务](http://tonybai.com/2015/03/14/selfhost-ngrok-service/)
   
  * [手把手教你搭建ngrok服务－轻松外网调试本机站点](https://aotu.io/notes/2016/02/19/ngrok/)   
      
      
      
      
      
      
