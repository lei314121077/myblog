# golang  构建工具之Makefile

Makefile 本身就是用来描述依赖的，可读性非常好，而且与强大的 shell 结合在一起，基本可以实现任何想要的功能

## Makefile支持的功能

* make build: 编译
* make vendor: 下载依赖
* make api: 生成协议代码
* make json: easyjson 代码生成
* make test: 运行单元测试
* make benchmark: 运行性能测试
* make stat: 代码复杂度统计，代码行数统计
* make clean: 清理 build 目录
* make deep_clean: 清理所有代码以外的其他文件
* make third: 下载所有依赖的第三方工具
* make protoc: 下载 protobuf 工具
* make glide: 下载 glide 依赖管理工具
* make golang: 下载 golang 环境
* make cloc: 下载 cloc 统计工具
* make gocyclo: 下载 gocyclo 圈复杂度计算工具
* make easyjson: 下载 easyjson 工具

[makefile文件指令](http://blog.sina.com.cn/s/blog_9b0604b40101rcxd.html)。

* -i 　　忽略命令执行返回的出错信息。
* -s 　　沉默模式，在执行之前不输出相应的命令行信息。
* -r 　　禁止使用build-in规则。
* -n 　　非执行模式，输出所有执行命令，但并不执行。
* -t 　　更新目标文件。
* -q　　 make操作将根据目标文件是否已经更新返回"0"或非"0"的状态信息。
* -p　　 输出所有宏定义和目标文件描述。
* -d　　 Debug模式，输出有关文件和检测时间的具体信息。

linux下make标志位的常用选项与Unix系统中稍有不同，下面我们只列出了不同部分：

* -c dir　　 在读取 makefile 之前改变到指定的目录dir。
* -I dir 　　当包含其他 makefile文件时，利用该选项指定搜索目录。
* -h 　　help文挡，显示所有的make选项。
* -w 　　在处理 makefile 之前和之后，都显示工作目录。









































