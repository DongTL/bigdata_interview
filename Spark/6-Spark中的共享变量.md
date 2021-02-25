# Spark中的共享变量

问题：

Spark程序中，当一个传递给spark的函数在集群上运行时，spark实际操作的是这个函数所用变量的一个副本，这些变量会被复制到每台机器上，并且这些集群上所有的更新默认都不会传回driver端。



因此Spark中设置了共享变量，用来解决这一通讯限制。

Spark提供有两种共享变量，**广播变量**与**累加器**。



- 广播变量

  - 高效分发较大的对象

  - 将对象分发到每个Executor上，Executor上的task会共享这个变量，需要时从Executor拉取

  - ```scala
    //创建broadcast变量，并将list的值存入
    val broadCast = sparkcontext.broadcast(list)
    
    //取出广播变量中的值
    broadCast.value
    ```

  - 变量只会被发到各个节点一次，并作为只读值处理，修改这个值不会影响到别的节点。

  - 广播变量只能在Driver端定义，不能在Executor端定义。

- 累加器

  - 对不同节点上的数据进行聚合

  - ```scala
    //创建accumulator并初始化为0
    val accumulator = sc.accumulator(0);
    
    //使用累加器
    val result = linesRDD.map(s => {
       accumulator.add(1) //有一条数据就增加1
       s
    })
    //取出累加器中的值
    accumulator.value
    ```

  - 累加器在Driver端定义赋初始值，并且只能在Driver端读取，在Excutor端更新。