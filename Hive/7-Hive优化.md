# Hive优化

## 1 大表join小表

大表与小表join时，将小表放在前面，因为hive会将前面的表进行缓存，这样效率更高。



## 2 小文件合并

在map阶段之前，使用`combineHiveInputFormat`对小文件进行合并，减少map数量。

- 列处理
  - 在SELECT时，禁止出现`select *`，只取需要的列
- 行处理
  - 在分区剪裁中，当使用外连



想到再补充