Mac自带Apache和PHP，但是没有MySQL，需要自己安装。

### Apache:
* `sudo apachectl start;` 启动Apchae。
	* `sudo apachectl －v;` 查看Apache版本。
* `http://localhost`查看Apache启动成功了。
	* 显示的文件路径是`/Library（资源库）/WebServer/Documents/”`下，这是Apache的默认根目录。

### PHP
* `sudo vi /etc/apache2/httpd.conf`打开Apache的配置文件。
* `#LoadModule php5_module libexec/apache2/libphp5.so` 取消注释。
* `sudo cp /etc/php.ini.default /etc/php.ini;` 把php.ini.default改名字为php.ini，并且修改php.ini。
	* `upload_max_filesize = 2M`
	* `post_max_size = 8M`
	* `display_errors = On`
* `sudo apachectl restart` 重启Apache。

### MySQL

* 点击运行dmg`mysql-5.1.46-osx10.6-x86_64.dmg`。
* 点击安装`mysql-5.1.46-osx10.6-x86_64.pkg`，安装路径是`/usr/local/mysql-5.1.46-osx10.6-x86_64`。
* `mysql -u root -p`, 运行mysql。
* 如果出现让你reset password的情况，运行`alter user 'root'@'localhost' identified by 'root';`

### phpMyAdmin
* 下载`phpMyAdmin-4.6.4-all-languages.zip`。
* 复制到`/Users/[用户名]/Sites`，解压，文件夹名字为`phpmyadmin`。
* 将里面的`config.sample.inc.php`重命名为`config.inc.php`。
* 修改`config.inc.php`，放开Cookie加密，随意的长字符串$cfg['blowfish_secret'] = ''; 


### 参考资料：
* http://blog.chinaunix.net/uid-22556372-id-3245808.html
* http://www.cnblogs.com/ToDoToTry/p/4401978.html


