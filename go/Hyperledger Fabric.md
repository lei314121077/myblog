# Hyperledger Fabric && 超级账本

## Hyperledger Fabric 环境安装与要求

* 1、docker 2、docker-compose 3、go 4、python
  
  需要通过Docker从网上拉取镜像，然后在容器里面运行
  
* 2、docker 容器 添加阿里云容器

```bashrc 

 vi /etc/docker/daemon.json
 {
    "registry-mirrors" : ["https://obou6wyb.mirror.aliyuncs.com"]  
 }
 
  docker pull hyperledger/fabric-tools:x86_64-1.0.0
  docker pull hyperledger/fabric-couchdb:x86_64-1.0.0
  docker pull hyperledger/fabric-kafka:x86_64-1.0.0
  docker pull hyperledger/fabric-zookeeper:x86_64-1.0.0
  docker pull hyperledger/fabric-orderer:x86_64-1.0.0
  docker pull hyperledger/fabric-javaenv:x86_64-1.0.0
  docker pull hyperledger/fabric-ccenv:x86_64-1.0.0
  docker pull hyperledger/fabric-ca:x86_64-1.0.0
  docker pull hyperledger/fabric-baseos:x86_64-0.3.1
  docker pull hyperledger/fabric-baseimage:x86_64-0.3.1
  docker pull hyperledger/fabric-membersrvc:latest
  
  docker pull hyperledger/fabric-kafka:latest
  docker pull hyperledger/fabric-zookeeper:latest

```

## excamples 示例

* 进入cli容器

```bashrc
 docker exec -it cli bash
```

### e2e_cli

* 运行与启动

```bashrc
# 目录
cd /home/ray/go/src/github.com/hyperledger/fabric/examples/e2e_cli

# 启动
./network_setup.sh up

# 结束
./network_setup.sh down

```


### [chaincode](https://www.cnblogs.com/zeyaries/p/7173028.html)

cd /home/ray/go/src/github.com/hyperledger/fabric-samples/chaincode-docker-devmode


* 启动网络

```bashrc
###删除所有活跃的容器###
docker rm -f $(docker ps -aq)
###清理网络缓存###
docker network prune
###启动
docker-compose -f docker-compose-simple.yaml up
```

* 启动chaincode容器

```bashrc
docker exec -it chaincode bash
```

* 启动cli容器

```bashrc
docker exec -it cli bash

参考
peer chaincode install -p chaincodedev/chaincode/你自己的链码文件名 -n mycc -v 0
peer chaincode instantiate -n mycc -v 0 -c '{"Args":["a","10"]}' -C myc
修改为20
peer chaincode invoke -n mycc -c '{"Args":["set", "a", "20"]}' -C myc
查询
peer chaincode query -n mycc -c '{"Args":["query","a"]}' -C myc


```




















  














