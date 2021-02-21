# Hive窗口函数

## OVER

Hive中通过`聚合函数`+`OVER()`，使用窗口函数对数据进行分析。

```sql
over(partition by xxx order by xxx[asc|desc])
```

over是用来决定以哪个字段进行分隔，以哪个字段来排序

前面的聚合函数用来决定执行什么操作



## 序列函数



- RANK() 排序相同会重复，总数不变（1,2,2,4）
- DENSE_RANK() 排序相同会重复，总数会减少（1,2,2,3）
- ROW_NUMBER() 排序相同会顺延 （1,2,3,4）

