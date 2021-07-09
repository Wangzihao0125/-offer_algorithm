# -offer_algorithm

# SQL事务

## 把多条语句作为整体进行操作的功能成为数据库事务

SQL数据库事务的四个特性ACID：

A：Atomic原子性，是指将所有SQL作为原子单元执行，要么全部执行，要么全部不执行

C: Consistent一致性，即完成事务后，所有数据的状态都是一致的，如果A减去了100，则B一定加上了100

I: Isolation隔离性，如果多个事务并发执行，则每个事务作出的修改必须与其他事务进行隔离。

D: Duration持久性，即事务完成后，对数据库数据的修改会被持久化存储。