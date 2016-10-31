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

### DCL：控制语句，grant、revoke...


### 其他：
* `show databases;`
* `use test1;`
* `show tables;`

