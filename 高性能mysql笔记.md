---
title: 高性能MYSQL
date: 2017-07-19 22:53:54
tags:
---

## 高性能MYSQL

> - 行级锁只在存储引擎层实现
> - 事务的隔离级别
>   - read uncommited: 问题——脏读:**一个事务会读进还没有被另一个事务提交的数据，所以你会看到一些最后被另一个事务回滚掉的数据**
>   - read commited:问题——不可重复读:**一个事务读进一条记录，另一个事务更改了这条记录并提交完毕，这时候第一个事务再次读这条记录时，它已经改变了**(解决：如果只有在修改事务完全提交之后才可以读取数据，可以避免该问题)
>   - repeatable read:问题——幻读:**一个事务用Where子句来检索一个表的数据，另一个事务插入一条新的记录，并且符合Where条件，这样，第一个事务用同一个where条件来检索数据后，就会多出一条记录**(解决:如果在操作事务完成数据处理之前，任何其他事务都不可以添加新数据，则可避免该问题)
>   - serializable
> - 死锁:innodb的处理——将持有最少行级排他锁的事务回滚
> - innodb下MVCC只在read commited 和 repeatable read 下适用

<!-- more -->