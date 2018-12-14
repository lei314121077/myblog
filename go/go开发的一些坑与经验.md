# 一些经验

* 思考：go里面是否可以有多个gopath

 答案是可以的

* 那么如何配置和管理多个gopath

首先你得配置好一个基础的gopath

然后我们假设你有多个gopath，那么在开发过程当中如何有效的应用gopath呢，在你的bashrc或者zshrc里面加入下面这段alias 
```bashrc
alias gopath='export GOPATH=`pwd`:$GOPATH'
```

然后在你新应用到的gopath目录输入gopath，如果还有2个以上的gopath怎么办，别担心拍下面这个命令解决问题

```bashrc
export GOPATH=`pwd`:$GOPATH
```


# grpc 

go get google.golang.org/grpc

   * 无法直接go get google.org/... 相关的依赖包

      ```bashrc
         package google.golang.org/grpc: unrecognized import path "google.golang.org/grpc"(https fetch: Get https://google.golang.org/grpc?go-get=1: dial tcp 216.239.37.1:443: i/o timeout)
      ```

   原因是这个代码已经转移到github上面了，但是代码里面的包依赖还是没有修改，还是google.golang.org这种，所以不能使用go get的方式安装

   * 解决
   
      ```
      git clone https://github.com/grpc/grpc-go.git $GOPATH/src/google.golang.org/grpc
      git clone https://github.com/golang/net.git $GOPATH/src/golang.org/x/net
      git clone https://github.com/golang/text.git $GOPATH/src/golang.org/x/text
      go get -u github.com/golang/protobuf/{proto,protoc-gen-go}
      git clone https://github.com/google/go-genproto.git $GOPATH/src/google.golang.org/genproto

      cd $GOPATH/src/
      go install google.golang.org/grpc
      ```
