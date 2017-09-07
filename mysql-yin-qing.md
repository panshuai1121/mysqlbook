## Mysql 存储引擎

在考虑存储引擎除非要用到某些InnoDB不具备的特性，默认都使用InnoDB作为存储引擎。



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

**Name：**表名

**Engine：**表的存储引擎类型，在旧版本里 该字段叫type。

**Version：**版本号

**Row\_format：**行的格式，MyISAM表 可选的值为Dynamic，Fixed或者Compressed，Dynamic的行长度是可变的，一般包含可变长度的字段，如vachar 或BlOB。Fixed的行长度则是固定的，只包含长度的列，如char 和INTEGER 。Copressed的行只在压缩表中存在。

**Rows：**

表中的行数，对于MyISAM和其他的一些存储引擎，该值是精确的，对于Innodb 来说该值是预估值。

**Avg\_**_**row\_length: **平均每行包含的字节数。_

**Data\_length**：表数据的大小（以字节单位）

**Max\_**_**data\_length: 表**数据的最大容量，该值跟存储引擎有关系_

**Index\_length**：索引的大小（字节为单位）

**Data\_free:**对于MyISAM表，表示已分配但目前没有使用的空间，这部分空间包括了之前删除的行，以及后续可以被INSERT利用到的空间。

**Auto\_increment**_ :下一个AUTO_\_INCREMENT的值

**Create\_time**:表创建的时间

**Update\_time**:表数据最后修改的时间

**Check\_time**:使用CKECK TABLE 命令或者myisamchk工具最后一次检查表的时间

**Collation**：表的默认字符集和字符列排序规则

**Checksum**：如果启动，保存是整个表的实时校验和

**Create\_options**:创建表时指定的其他选项

**Comment**：该列包含了一些其他信息，_对于MyISAM表，保存的是创建时带的注释，对于InnoDB 保存的是innoDB表空间的剩余空间信息，如果是一个视图，则该列包含“VIEW”的文本字样_

