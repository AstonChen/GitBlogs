### 命令：
* `mysql -u root -p` 连接MySQL。
* `;`或者`\g` 结束命令行。
* `\c` 清除sql语句。
* 


### DDL：定义语句，create、drop、alter...
* `CREATE DATABASE test1;`
* `USE test1;`
* `SHOW tables;`
* `DROP DATABASE test1;` 删除数据库。
* 创建表：
	
	```php
	CREATE TABLE tablename(
		c1 char(20) not null,
		c2...
	);
	```
* `DESC tablename;` 查看表。
* `SHOW CREATE TABLE tablename;` 查看表的创建语言。	

### DML：操作语句，insert、delete、update、select...

### DCL：控制语句，grant、revoke...


### 其他：
* `show databases;`
* `use test1;`
* `show tables;`

