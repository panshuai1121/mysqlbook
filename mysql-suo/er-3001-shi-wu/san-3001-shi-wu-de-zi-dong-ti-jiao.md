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

1 或者 ON 表示启动，0 或 OFF表示禁用

