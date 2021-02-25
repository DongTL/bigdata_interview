# SparkSQL中的RDD/DataFrame/DataSet

## RDD

- 优点：
  - 有泛型，编译时类型安全
  - API具有面向对象的编程风格
- 缺点：
  - 没有Schema，导致集群间建通讯、IO时，数据以及对象结构都需要进行序列化与反序列化，导致性能开销大
  - 频繁的创建和销毁对象，势必会增加GC

## DataFrame

- 优点：
  - DataFrame增加了Schema，Spark通过Schema就能获取对象结构，在通讯和IO时无需再对对象结构进行序列化与反序列化
  - 引入了off-heap（堆外内存），可快速操作数据，避免大量GC
- 缺点：
  - 没有泛型，编译时不安全
  - API不是面向对象风格

## DataSet

- 优点：
  - 结合了RDD与DF的优点，既有泛型，也有Schema
  - 引入Encoder概念，当序列化时，Encoder产生的字节码与off-heap进行交互，能够达到按需访问数据的效果，而不用反序列化整个对象。

