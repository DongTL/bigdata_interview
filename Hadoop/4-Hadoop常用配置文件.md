# Hadoop常用配置文件

- hadoop-env.sh:
  - 用于定义Hadoop运行环境相关的配置信息，如JAVA_HOME，hadoop的JVM指定特定的选项，指定日志文件所在的目录路径以及master和slave文件位置等
- core-site.xml：
  - 用于定义系统级别的参数，如HDFS URL，Hadoop临时目录，rack-aware集群中的配置文件的配置等，此文件中的参数会覆盖core-default.xml文件中默认的配置
- hdfs-site.xml:
  - HDFS的相关设置，如文件副本个数、块大小以及是否使用强制权限等，此文件中的参数会覆盖hdfs-default.xml文件中的默认配置
- mapred-site.xml:
  - MapReduce的相关设置，如reduce任务的默认个数、任务所能够使用内存的默认上下限等，此文件中的参数会覆盖mapred-default.xml文件中的默认配置

