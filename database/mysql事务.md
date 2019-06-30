# MySql事务总结

​       

①参考书籍:高性能mysql  
②参考视频:鲁班学院mysql索引以及事务(地址:https://www.bilibili.com/video/av57156557)
③参考博客:https://blog.csdn.net/qq_38538733/article/details/88902979



1. 什么是mysql事务？
   事务指的是单个逻辑工作单元执行的一系列操作。mysql 的事务就是一组sql操作(注:增删改查)

2. 事务的特点=>ACID

   1. 原子性(A:atommicity)
      不能分割的最小工作单位。sql操作要么全部成功，要么全部失败
   2. 一致性(C:consistency)
      事务执行完毕，数据库总是从一个状态转化至另外一个状态。
   3. 隔离性(I:isolation)
      一个事务执行成功与否和执行过程，对其他事务不影响
   4. 持久性
      事务一旦执行完毕，数据会永久性的保存在数据库中

3. 如何启动，提交，回滚事务以及自动提交

   ```mysql
   begin;	#开启事务
   rollback; #回滚事务
   commit;  #提交事务
   
   mysql> # 每一条查询操作都是默认开启事务的。除非手动开启一个事务(begin)
   mysql> show variables like 'AUTOCOMMIT'; #自动提交
   +---------------+-------+
   | Variable_name | Value |
   +---------------+-------+
   | autocommit    | ON    |     #默认开始
   +---------------+-------+
   1 row in set, 1 warning (0.00 sec)
   
   ```

   

4. 隔离级别

   ```mysql
   select @@tx_isolation #当前会话的隔离级别
   select @@global.tx_isolation # 系统当前的隔离级别
   set session transaction isolation level repeatable read; #设置当前会话的隔离级别
   set global transaction isolation level repeatable read; #设置系统的隔离级别
   ```

   多版本并发控制

   ![1561899452757](assets/1561899452757.png)

   ​		版本链：每当有一个事务修改某条记录，就复制一份记录用于保存修改的值，并且同时记录两个字段(trx_id,roll_pointer)。trx_id记录事务的id，roll_pointer指向上个事务修改保留的记录(如果是第一个事务修改这记录，则指向原始的那条记录)。

   对于read uncommited ，直接读取版本链的最新数据。

   对于serializable，加锁的方式访问数据库

   对于使用`READ COMMITTED`和`REPEATABLE READ`需要通过ReadView进行判断去读取版本链上的数据

- Readview
  		活跃的读写事务，把它们的事务id放到一个列表中，我们把这个列表命名为为`m_ids`。
  - 被访问版本的trx_id比m_ids都要小，该版本可以被当前事务访问。
  - 被访问版本的`trx_id`比`m_ids`列表中最大的事务id 都要大，该版本的事务在生成`ReadView`后才生成，该版本不可以被当前事务访问
  -  被访问版本的`trx_id`在m_ids列表的最大事务id，最小事务id之间，



​	



隔离的四个级别

1. 读未提交	read uncommited

   一个事务可以读取到其他事务尚未提交的数据

   一个事务如果对数据有修改，但这个事务尚未提交。修改的数据可以被其他事务读取到。但是这些数据对其他事务来说，可能不是准确的。这样的情况就叫做，脏读。

   ```mysql
   # 假如有记录如下
   mysql> select * from user where id = 1;
   +----+------+------+--------+
   | id | name | role | status |
   +----+------+------+--------+
   |  1 | A    | 1    |      1 |
   +----+------+------+--------+
   事务A和事务B同时进行
   
   +----+-------------+------------+--------+
   |    | 事务A        |事务B       | status |
   +----+-------------+------------+--------+
   |  1 | begin       | begin      |      1 |
   +----+-------------+------------+--------+
   |  2 |             |set status=2|      2 |
   +----+-------------+------------+--------+
   |  3 |select status|            |        |
   |    |(status=2)   |            |      2 |
   +----+-------------+------------+--------+
   |  4 |             |rollback    |       1|
   +----+-------------+------------+--------+
   |  5 |commit       |            |       1|
   +----+-------------+------------+--------+
   如果事务B将status设置成2，事务A可以读到其他事务修改未提交事务的值(就是status=2)。然后事务B回滚事务，status值回滚成1.那么事务A读取到的status=2就是不存在的值，被污染的值。这种情况就是脏读
   
   ```

   

2. 读已提交    read commited
   一个事务读取到数据只能是另一个事务已经提交完的数据。

3. 可重复读 repeatable read
   一个事务第一次读到某条记录后，即使其他事务修改了该记录的值并且提交，该事务下次读取这条记录还是第一次读取的值。还是会出现幻读