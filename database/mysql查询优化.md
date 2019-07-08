# select 优化

1. select优化的方式，试用于update和delete
2. 常量表达式被索引使用的时候，只计算一次。
3. 表引擎MyIsam和MEMORY,使用count(*)不带with条件，不会全表扫描而是直接表信息表去读信息。
4. 尽可能地发现一些无效常量表达，并更正。mysql会非常快检测到有些表达式是不可能的，然后不返回记录。
5. `WHERE`查询中发现未使用`GROUP BY`或者`聚合函数(比如COUNT(),MIN()等)`，那么`HAVING`会与`WHERE`合并
6. 多表查询中，`MYSQL`会对表进行评估从而构造出更简单的查询

