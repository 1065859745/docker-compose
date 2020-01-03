# docker-hadoop
创建一主三从hadoop集群（创建其他方式的集群可在docker-compose.yml文件中添加）
# 修改脚本执行用户
## 路径：$HADOOP_HOME/bin
## hadoop,hdfs,yarn,mapred文件中
```
HADOOP_SHELL_EXECNAME="root"
```
# 修改hadoop配置
## 路径：$HADOOP_HOME/etc/hadoop
## core-site.xml
```
<property>
    <name>fs.defaultFS</name>
    <value>hdfs://hadoop-master1:9000</value>
</property>
```
## hadoop-env.sh 配置jdk路径、hadoop路径、执行脚本的用户等
修改以下配置
```
JAVA_HOME=/java
export HADOOP_HOME=/hadoop
export HADOOP_CONF_DIR=${HADOOP_HOME}/etc/hadoop
export HADOOP_LOG_DIR=/logs
export HDFS_DATANODE_SECURE_USER=root
export HDFS_NAMENODE_USER=root
```
## hdfs-site.xml
```
<property>
    <name>dfs.replication</name>
    <value>2</value>
</property>
```
## mapred-site.xml
```
<property>
    <name>mapreduce.framework.name</name>
    <value>yarn</value>
```
## workers
```
hadoop-master1
hadoop-slave1
hadoop-slave2
```
# 配置hadoop路径
在docker-compose.yml文件中修改volumn下的hadoop目录修改为本机上hadoop目录（修改冒号左边的路径）
# 配置jdk路径
在docker-compose.yml文件中修改volumn下的docker-java-home目录修改为本机上jdk目录（修改冒号左边的路径）
# 在该目录下执行
```
docker-compose up -d
```
# 在hadoop-master1容器中执行
格式化分布式文件系统
```
bin/hadoop namenode -format
```
# 启动hadoop集群
```
sbin/start-all.sh
```