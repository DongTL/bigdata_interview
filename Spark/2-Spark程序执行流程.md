# Spark程序执行流程

![spark-submit-flow](2-Spark程序执行流程.assets/spark-submit-flow.bmp)

以YARN模式为例：

1. SparkSubmit提交Application到Driver端
2. Driver执行Application，创建SparkContext
3. SparkContext解析Application：RDD->DAG->task
4. Driver向ResourceManager注册程序并申请资源
5. ResourceManager分配资源给NodeManager，启动Executor
6. Executor向Driver端申请task，Driver将task分配给Executor执行
7. Executor执行任务后，通过心跳机制向ResourceManager报告执行过程与结果
8. 执行结束后Executor向SparkContext报告执行结果，SparkContext向ResourceManager报告并释放资源



备注：

client模式下，Driver执行在client中

cluster模式下，Driver执行在NodeManager中的AppMaster中