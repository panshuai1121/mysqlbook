### MVCC

MVCC \(Multiversion Concurrency Control\),即多版本并发控制技术,它使得大部分支持行锁的事务引擎,不再单纯的使用行锁来进行数据库的并发控制,取而代之的是,把数据库的行锁与行的多个版本结合起来,只需要很小的开销,就可以实现非锁定读,从而大大提高数据库系统的并发性能.

Innodb的MVCC，是通过在每行记录后边保存了两个隐藏的列来实现的，这两个列，一个保存了行的创建时间，一个保存行得过期时间（或删除时间），注意这个时间并不是时间值，而是系统版本号。每一个事务开始，系统版本号会自动递增。

---

### MVCC 具体操作

SELECT

1. InnoDB 只查找版本号早于当前事务版本的数据行，这样可以确保事务读取的行，要么在事务开始前已经存在，要么是事务本身插入或修改过的。
2. 行的删除版本要么没有定义，要么大于当前事务版本号。

INSERT

Innodb 为新插入的每一行保存当前系统版本号作为行版本号。

DELETE

Innodb 为删除的每一个行保存当前系统版本号作为行删除标识。

UPDATE

Innodb 为插入一条新纪录，保存当前系统版本号作为行版本号，同时保存当前系统版本号到原来得行作为删除标识。

优点：

保存两个额外系统版本号，使得大多数 读操作都可以不用加锁，这样让数据操作变得简单 、性能好。

缺点：

每行纪录需要额外的存储空间，需要做更多行的检查，以及维护工作。

**MVCC 只在 REPATABLE READ ， READ COMMITED 两个级别下工作。**

