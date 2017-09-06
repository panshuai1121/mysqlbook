## 事务的自动提交

Mysql 默认采用自动提交（AUTOCOMMIT）

```
mysql> SHOW VARIABLES LIKE 'AUTOCOMMIT';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| autocommit    | ON    |
+---------------+-------+

mysql> set AUTOCOMMIT = 1;
Query OK, 0 rows affected (0.00 sec)

```



