# docker-redis-cluster
在该目录下执行下面来启动redis主从节点容器
```
docker-compose up -d
```
在创建的redis-master1容器中执行以下命令创建3主节点3从节点的redis集群(命令中的ip修改为你的机器的ip)
```
redis-cli --cluster create 192.168.99.100:6391 192.168.99.100:6392 192.168.99.100:6393 192.168.99.100:6394 192.168.99.100:6395 192.168.99.100:6396 --cluster-replicas 1
```