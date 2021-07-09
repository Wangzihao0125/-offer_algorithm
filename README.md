# -offer_algorithm

# SQL事务

## 把多条语句作为整体进行操作的功能成为数据库事务

SQL数据库事务的四个特性ACID：

A：Atomic原子性，是指将所有SQL作为原子单元执行，要么全部执行，要么全部不执行

C: Consistent一致性，即完成事务后，所有数据的状态都是一致的，如果A减去了100，则B一定加上了100

I: Isolation隔离性，如果多个事务并发执行，则每个事务作出的修改必须与其他事务进行隔离。

D: Duration持久性，即事务完成后，对数据库数据的修改会被持久化存储。

# StringBuilder

由于String在进行拼接时会产生新的字符串，为了避免费时和费空间，引入了StringBuilder，可以随时添加新的子串，并在合适的时候toString()转化为字符串。

<Strong> 前身是StringBuffer,它的效率低，但是允许多线程执行添加或删除。如果所有字符串都在单线程中编辑，则直接使用StringBuilder.
