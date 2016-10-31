### 命令：
* `mysql -u root -p` 连接MySQL。
* `;`或者`\g` 结束命令行。
* `\c` 清除sql语句。

### DDL：定义语句，create、drop、alter...
* 创建：
	* `CREATE DATABASE database_name;` 创建数据库。
	* 创建表：
		
		```php
		CREATE TABLE table_name(
			c1 char(20) not null,
			c2 ...
		);
		```
* 删除：
	* `DROP DATABASE database_name;` 删除数据库。
	* `DROP TABLE table_name;` 删除表。
* 修改：
	* `ALTER TABLE table_name MODIFY c1 char(50);` 把c1列的类型修改为char(50)。
	* `ALTER TABLE table_name MODIFY c1 char(50) FIRST;` 把c1列的类型修改为char(50)。顺便放在表首。
	* `ALTER TABLE table_name ADD c4 char(20) BEFORE c5;` 把c4 char(20)列添加到c5前面。
	* `ALTER TABLE table_name ADD COLUMN c2 char(20) not null;` 增加一列在表的后面。
	* `ALTER TABLE table_name DROP COLUMN c3;` 删除c3列。
	* `ALTER TABLE table_name CHANGE c2 c3 int(4);` 修改c2的名字为c3，而且格式为int。
	* `ALTER TABLE table_name1 RENAME table_name2;` 把表名改为table_name2。
* 其他：
	* `USE database_name;` 使用数据库。
	* `SHOW tables;`* `DESC table_name;` 查看表。
	* `SHOW CREATE TABLE table_name;` 查看表的创建语句。

### DML：操作语句，insert、delete、update、select...
* 插入：
	* `INSERT INTO table_name VALUES (value1, value2...);`
* 更新：
	* `UPDATE table_name SET age=26 WHERE name='chenjian';`
* 删除：
	* `DELETE FROM table_name WHERE age=26;`
* 查询：
	* `SELECT * FROM table_name;`
	* `SELECT * FROM table_name WHERE name='chenjian';`
	* `SELECT * FROM table_name ORDER BY name ASC|DESC;` 按照age生序降序排列。
	* `SELECT * FROM table_name ORDER BY name, age ASC|DESC;` 按照name生序降序排列，如果一样就按age排序。
	* `SELECT * FROM table_name limit 1,3;` 从第2条开始取3条。
	* `SELECT COUNT(*) FROM table_name;` 取出记录数。
	* `SELECT age, count(1) FROM table_name GROUP BY age;` 以age分类，取出每种age的数量。
	* `SELECT age, count(1) FROM table_name GROUP BY age WITH ROLLUP;` 以age分类，取出每种age的数量, 同时计算不同age分类的总数量值。
	* `SELECT age, count(1) FROM table_name GROUP BY age HAVING age>26;` 以age分类，取出每种age大于26的数量。
	* `SELECT MAX(age), MIN(age), SUM(age),AVG(age) FROM table_name;`
* 内连接：仅选出两张表中互相匹配的记录。
	* `SELECT A.*, B.* FROM A,B WHERE A.id=B.id;` 仅取出相等的值。
	* `SELECT A.*, B.* FROM A INNER JOIN B ON A.id=B.id;` 仅取出相等的值。
* 外连接：全部取出来匹配,包括（左连接，右连接）。
	* 左连接：包含左表中所有的数据，甚至在右表中不匹配的数据。
	* 右连接：包含右表中所有的数据，甚至在左表中不匹配的数据。
	* `SELECT A.*,B.* FROM A LEFT JOIN B ON A.id=B.id;` 
	* `SELECT A.*,B.* FROM A RIGHT JOIN B ON A.id=B.id;` 
* 子查询：
	* `SELECT * FROM A WHERE id in (SELECT id FROM B);` A的id只要在B中有，就列出来。
* 记录联合：UNION ALL将结果直接合并，UNION会去重。
	* `SELECT id FROM A UNION ALL SELECT id FROM B;` 把A和B中的id合并。
	* `SELECT id FROM A UNION SELECT id FROM B;` 把A和B中的id合并，重复的删除掉。

### DCL：控制语句，grant、revoke...
### count(1)与count(*)比较：	
	 
* 如果你的数据表没有主键，那么count(1)比count(*)快。
* 如果你的表只有一个字段的话那count(*)就是最快的啦。

### 数据类型：

|类型|字节|范围|备注|
| --- |---| ---|---|
|TinyInt|1|有符号：-128～127<br>无符号：0～225||
|SmallInt|2|有符号：-32768～21767<br>无符号：0～65535||
|MediumInt|3|有符号：-8388608～8388607<br>无符号：0～1677215||
|Int, Integer|4|有符号：-2147483648～2147483647<br>无符号：0～4294967295||
|BigInt|8|有符号：-9223372036854775808～9223372036854775807<br>无符号：0～18446744073709551615||
|||||
|||||
|||||



