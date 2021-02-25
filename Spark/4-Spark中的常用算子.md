# Spark中的常用算子

## 算子分类

Spark中的算子分为两大类，Transformation算子与Action算子：

- Transformation算子
  - 不立即触发作业提交，用于完成作业中间处理过程
  - 返回一个新的RDD
- Action算子
  - 立即触发程序提交执行
  - 不返回RDD（可能返回除RDD外的其他类型数据，也可能无返回值）



## 常见算子举例

### Transformation算子

#### value数据类型

- 输入分区与输出分区一对一型
  - map
  - flatmap
  - mapPartitions
  - sortBy

- 输入分区与输出分区多对一型

  - union
  - cartesian

- 输入分区与输出分区多对多型

  - groupBy
  - groupByKey

- 输出分区为输入分区子集型

  - filter
  - distinct
  - subtract

#### key-value数据类型

- 输入分区与输入分区一对一型
  - mapValues
- 对单个RDD或两个RDD聚集
  - combineByKey
  - reduceByKey
  - partitionBy
- 连接
  - 各种join

### Action算子

- 无输出
  - foreach
- 文件操作
  - saveAsTextFile等
- Scala集合和数据类型操作
  - reduce
  - collect
  - top
  - first
  - take
  - count
  - countByKey



## 补充：会产生shuffle的算子

- reduceByKey
- groupByKey
- ...ByKey

> 补充：
>
> reduceByKey比groupByKey更安全
>
> reduceByKey在进行shuffle之前会对数据进行预聚合，可以减少shuffle的数据量，一定程度上防止OOM。