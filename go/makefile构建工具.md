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










































