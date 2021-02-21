# Hive UDF

Hive中通过UDF（用户自定义函数）可以让用户自行对HiveQL的功能进行扩展。

UDF又分为UDAF（用户自定义聚合函数）与UDTF（用户自定义表生成函数）。

- 自定义UDF：继承`UDF`类，重新`evaluate`方法
- 自定义UDTF：继承`GenericUDTF`类，重写`initialize`、`process`、`close`三个方法。