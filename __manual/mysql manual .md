## 一、基础篇：
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
|Float|4|||
|Double|8|||
|Decimal(M, D)|M+2|||
|char|M|0~255||
|varchar||0~65535||
|||||
|||||



### 时间：
* `DATE;` YYYY-MM-DD
* `TIME;` HH:MM:SS
* `DATETIME;` YYYY-MM-DD HH:MM:SS
* `TIMESTAMP;` YYYYMMDDHHMMSS
* `YEAR;` YYYY
* `now();` 当前DATETIME。

### 常用函数：
* `concat(s1, s2, s3...);` 连城一个整的字符串。
* `insert(str, x, y, instr);` 把str从第x位开始到y个长度换成instr。
* `lower(str);` 变小写。
* `upper(str);` 变大写。
* `left(str, x);` 返回左边x个字符串。
* `right(str, x);` 返回右边x个字符串。
* `lpad(str, n, pad);` 对str左边进行填充，直到n个字符长度。
* `rpad(str, n, pad);` 对str右边进行填充，直到n个字符长度。
* `ltrim(str);` 去掉左侧空格。
* `rtrim(str);` 去掉右侧空格。
* `repeat(str, x);` 把str重复x次。
* `replace(str, a, b);` 把str中的a换成b。
* `strcmp(s1, s2);` 比较s1和s2.
* `trim(str);` 去掉首位空格。
* `substring(str, x, y);` 返回str中从x位置起y个字符长度。
* `abs(x);` 取x的绝对值。
* `ceil(x);` 返回大于x的最小整数。
* `floor(x);` 返回小于x的最大整数。
* `mod(x, y);` 返回x/y的值。
* `rand();` 返回0～1之间的随机值。
* `round(x, y);` 返回x的四舍五入的y位小数的值。
* `truncate(x, y);` 返回x，但是只保留y位小数。
* `curdate();` 当前日期。
* `curtime();` 当前时间。
* `now();` 当前日期和时间。
* `unix_timestamp(now());` 当前时间戳。 
* `if(value, t f);` value是真的话，返回t，否则返回f。
* `isnull(value1, value2);` 如果value1不为空就返回value1，否则返回value2。`
* `database();` 当前数据库。
* `version();` 当前数据库版本。
* `user();` 登陆者的用户名。
* `MD5();` md5加密。
* `(, );`
* `(, );`


### PS:
* `int`与`int(5) zerofill;` int(5)要求最少5个位子，没有填充满就用0来填充，超过了就算了。
* `PRIMARK KEY(id, name);` 定义主键。
* `decimal(M, D)`比float、double更精细，存储货币等。M表示整数加小数位，D表示小数位。如果用于数据库等迁移最好不要这样使用，float、double不指定参数时候精度由操作系统、硬件等支持。decimal默认10位整数，0位小数位。
* `char`与`varchar`：char长度固定，0～255。varchar长度可变，0～65535。char(4),varchar(4)只能插入4个字符。
* `binary`与`varbinary`：只能包含二进制字符串。
* 正则表达式：`regexp`，`SELECT name FROM table_name WHERE name REGEXP 'jian';` 查找name里面有jian的数据。


## 二、开发篇：
* `CREATE TABLE table_name(.,.,.,.) ENGINE=引擎名字;` 引擎名字有：`Innodb`、`MyISAM`等。
* `ALTER TABLE table_name ENGINE=引擎名字;`
* `MyISAM` 不支持事务和外键，但是速度快。
* `Innodb` 支持提交、回滚、崩溃恢复能力的事物安全。但是效率差，占用更多的磁盘空间用来保留数据和索引。
	* `auto_increment` 自动增加列必须是索引。
	* `prmary key(id, name);` 把id、name设为主键。
	* `key 别名(column);` 设立column为索引，且取个别名。
	* `	constraint `fk_B_A` FOREIGN KEY (id) REFERENCES A(id);`  在B表上面运行，把B表的id上创建一个外键，连接到A表的id，如果删除A表的id会提示错误。
	* `alter table B drop foreign key fk_B_A;` 把B表中的外键删除掉。
	* `	alter table B add FOREIGN KEY (B.id) REFERENCES A(A.id) on delete cascade on update cascade;` 在B表上面运行，把B表的id上创建一个外键，连接到A表的id，如果删除A表的id，B表中使用这个id的就会都被删除。


## 三、优化篇：

## 四、管理维护篇：

## 五、架构篇：


