# Hadoop架构

Hadoop2.0版本之后主要由两部分组成

- HDFS：Hadoop分布式文件系统
- YARN：统一的资源调度平台



## HDFS

- NameNode：HDFS中的主节点，管理HDFS集群，存储元数据
- SecondaryNameNode：定期从NameNode拉取fsimage与editlog，合并文件后形成新的fsimage传回NameNode，辅助NameNode管理元数据
- DataNode：HDFS中的从节点，负责存储与读写数据



## YARN

- ResourceManager：YARN的主节点，接收客户端提交的任务请求，对任务进行资源分配。
- NodeManager：YARN平台的从节点，接收并执行任务。