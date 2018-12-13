# 超级账本

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

###启动节点###
CORE_PEER_ADDRESS=peer:7052 CORE_CHAINCODE_ID_NAME=mycc:0 ./raycd    # raycd是你编译过后的二进制文件名
###如果失败，把"7052"改为"7051"试试看

```

* 启动cli容器与[peer命令行](https://blog.csdn.net/sinat_36742186/article/details/79541855)

```bashrc

docker exec -it cli bash

参考
peer chaincode install -p chaincodedev/chaincode/{你自己的链码文件名} -n mycc -v 0
peer chaincode instantiate -n mycc -v 0 -c '{"Args":["a","10"]}' -C myc
#在CLI内部会为mychaincode创建SignedChaincodeDeploymentSpec，并将其发送到本地peer节点。这些节点会调用LSCC上的Install方法。上述的-p选项指明chaincode的路径，其必须在用户的GOPATH目录下（比如$GOPATH/src/sacc）。

修改为20
peer chaincode invoke -n mycc -c '{"Args":["set", "a", "20"]}' -C myc
查询
peer chaincode query -n mycc -c '{"Args":["query","a"]}' -C myc
```


# Hyperledger Fabric 

* What's Chaincode And Hyperledger Fabric

链码（chaincode）是 Hyperledger Fabric 提供的智能合约，是上层应用与底层区块链平台交互的媒介。

## 组件

* Channel：

是一种数据隔离机制，保证交易信息只有交易参与方可见，每个channel是一个独立的区块链，这使得多个用户可以共用同一个区块链系统而不用担心信息泄露问题。

* Chaincode：

也叫智能合约，将资产定义和资产处理逻辑封装成接口，当其被用户调用的时候，改变账本的状态。

* Ledger：

区块链账本，保存交易信息和智能合约代码。

* Network：

交易处理节点之间的P2P网络，用于维持区块链账本的一致性。

* Ordering service：

利用kafka、SBTF等共识算法对所有交易信息进行排序并打包成区块，发给committing peers节点，写入区块链中。

* World state：

显示当前资产数据的状态，底层通过LevelDB和CouchDB数据库将区块链中的资产信息组织起来，提供高效的数据访问接口。

* Membership service provider（MSP）：

管理认证信息，为client和peers提供授权服务。


















  














