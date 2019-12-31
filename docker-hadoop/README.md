# docker-hadoop
# 第一步：生成hadoop镜像
在该目录下执行
```
docker build -t hadoop .
```
# 创建一主三从hadoop集群（创建其他方式的集群可在docker-compose.ymlw文件中添加）
在该目录下执行
```
docker-compose up -d
```
# 修改hadoop配置文件
在该目录下 hadoop-3.2.1/etc/hadoop 为配置文件目录