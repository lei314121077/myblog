# 一些技巧笔记
 
 * 包导入
    ```golang
    在包前面加下划线表示，只执行该包的init初始化函数，其它不执行
    import (
       _ "github.com/astexie/beego"
    )
    
    ```
 * 变量
   常量加":="表示该变量只在函数内部可用
    ```golang
       a := "hello"
    ```
 * 接口
 
 
 
 
# 踩过的一些坑
