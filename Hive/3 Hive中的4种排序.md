# Hive中的4种排序比较
## sort by
- 数据进入reduce阶段前进行排序
- 数据仅在分区内有序

## order by
- 数据最终在一个reduce中进行排序
- 数据全局有序
- 数据量大时排序效率低

## distrbute by
- 按照指定字段将数据划分到不同的reduce中
- 通常和`sort by`配合使用，但要注意`distribute by`必须放在前面

## cluster by
- 一个特殊的`distribute by` + `sort by` 
- 但只能实现升序排列，不能指定`asc`或`dese`