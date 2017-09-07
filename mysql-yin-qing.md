## Mysql 存储引擎

可以使用SHOW TABLE STATUS LIKE ‘表名’ 进行查看。

```
mysql> SHOW TABLE STATUS LIKE 'user' \G;
*************************** 1. row ***************************
           Name: user
         Engine: MyISAM
        Version: 10
     Row_format: Dynamic
           Rows: 6
 Avg_row_length: 66
    Data_length: 396
Max_data_length: 281474976710655
   Index_length: 2048
      Data_free: 0
 Auto_increment: NULL
    Create_time: 2017-08-18 03:18:45
    Update_time: 2017-08-18 03:19:24
     Check_time: NULL
      Collation: utf8_bin
       Checksum: NULL
 Create_options:
        Comment: Users and global privileges
1 row in set (0.00 sec)
```

Name：表名

Engine：表的存储引擎类型，在旧版本里 该字段叫type。

Version：版本号

Row\_format：行的格式，MyISAM表 可选的值为Dynamic，Fixed或者Compressed，Dynamic的行长度是可变的，一般包含可变长度的字段，如vachar 或BlOB。Fixed的行长度则是固定的，只包含长度的列

