1. **information_schema 表介绍** 

第一个查询看看库里有多少个表，表名等
select * from INFORMATION_SCHEMA.TABLES

information_schema这张数据表保存了MySQL服务器所有数据库的信息。如数据库名，数据库的表，表栏的数据类型与访问权限等。

再简单点，这台MySQL服务器上，到底有哪些数据库、各个数据库有哪些表，每张表的字段类型是什么，各个数据库要什么权限才能访问，等等信息都保存在information_schema表里面。

Mysql的INFORMATION_SCHEMA数据库包含了一些表和视图，提供了访问数据库元数据的方式。

元数据是关于数据的数据，如数据库名或表名，列的数据类型，或访问权限等。有些时候用于表述该信息的其他术语包括“数据词典”和“系统目录”。

 

下面对一些重要的数据字典表做一些说明：

SCHEMATA表：提供了关于数据库的信息。

TABLES表：给出了关于数据库中的表的信息。

COLUMNS表：给出了表中的列信息。

STATISTICS表：给出了关于表索引的信息。

USER_PRIVILEGES表：给出了关于全程权限的信息。该信息源自mysql.user授权表。

SCHEMA_PRIVILEGES表：给出了关于方案（数据库）权限的信息。该信息来自mysql.db授权表。

TABLE_PRIVILEGES表：给出了关于表权限的信息。该信息源自mysql.tables_priv授权表。

COLUMN_PRIVILEGES表：给出了关于列权限的信息。该信息源自mysql.columns_priv授权表。

CHARACTER_SETS表：提供了关于可用字符集的信息。

COLLATIONS表：提供了关于各字符集的对照信息。

COLLATION_CHARACTER_SET_APPLICABILITY表：指明了可用于校对的字符集。

TABLE_CONSTRAINTS表：描述了存在约束的表。

KEY_COLUMN_USAGE表：描述了具有约束的键列。

ROUTINES表：提供了关于存储子程序（存储程序和函数）的信息。此时，ROUTINES表不包含自定义函数（UDF）。

VIEWS表：给出了关于数据库中的视图的信息。

TRIGGERS表：提供了关于触发程序的信息。