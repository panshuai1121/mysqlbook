## InnoDB存储引擎

InnoDB是Mysql的默认事务引擎，用来处理大量短期事务，InnoDB的数据存储在表空间（tablespace）中，表空间是由InnoDB管理的一个黑盒子，由一系列得数据文件组成，在MySQL 4.1以后的版本中，Innodb可以将每个表的数据和索引存放在单独的文件中。

InnoDB表基于聚簇索引创建，

