## MyISAM

在5.1和之前版本 mysql的默认存储引擎，提供大量的特性全文索引、压缩、空间函数（GIS）等，不支持事务和行级锁，缺陷是崩溃后无法安全恢复 。

MyISAM会将表数据存储在两个文件：数据文件和索引文件。分别以.MYD .MYI为扩展名。**MySAIM 表可以存储行记录数。**

在Mysql 5.0中，MySAIM表如果是变长行，则默认配置只能处理256T的数据，因为指向数据记录的指针长度是6个字节

更早的版本，指针长度4个字节，所以只能处理4GB的数据，而后所有版本MYSQL版本都支持8个字节的指针。

**要改变MySAIM表的指针长度（高或低）可以通过修改表的MAX\_ROWS 和AVG\_ROW\_LENGTH选项的值来实现，两者相乘就是表可能达到的最大大小，修改者两个参数会导致整个表的索引重建，可能需要很长时间完成**



    CREATE TABLE `weather` (
      `id` int(10) unsigned NOT NULL,
      `content` longtext NOT NULL,     #这个数据类型加上下面的设置，可以导入超大文本数据        
      PRIMARY KEY (`id`)
    ) ENGINE=MyISAM DEFAULT CHARSET=utf8 MAX_ROWS=750000 AVG_ROW_LENGTH=19000;


    alter table weather max_rows = 200000000000 avg_row_length = 50;



