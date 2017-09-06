## 事务

简单的来说，事务内的语句，要么全部执行，要么全部执行失败。

例子：假设某银行存在两张数据表，一张支付表和一张存储表，现在要从支付表中转移某一用户的100元金额。

操作步骤：

1. 检查支付账户是否有余额100元
2. 从支付表中减去100元
3. 增加到存储账户中100元

这三个步骤也就是事务，如果失败时则全部失败，必须回滚所有步骤。

```
#可以使用START TRANSACTION 开始一个事务，然后使用COMMIT提交事务将修改的数据持久保留，要么使用ROLLBACK撤回所有得修改

1、START TRANSCRTION
2、SELECT balace FROM checking WHERE customer_id = 987123;
3、UPDATE checking SET balance = balance-100.00 WHERE customer_id = 987123;
4、UPDATE savings SET balnace = balance + 200.00 WHERE customer_id = 987123;
5、COMMIT；
```

## ACID

原子性（atomicity）：

一个事务必须被视为一个不可分割的最小单元，整个事务中所有的操作要么提交成功，要么全部回滚对于一个事务，对事物来说不能只执行其中的一部分就是事务的原子性。

一致性（consistency）：

数据库从一个一致性的状态转换到另一个一致性的状态，也就是比如说上边的例子执行过程中某一条出现问题时，因为事务并未提交，所以事务中所修改的数据也不会保存到数据库中。

隔离性（isolation）：

一个事务所做的修改在最终定义之前，对其他事务不可见。\(详见隔离级别\)

持久性（durability）：

