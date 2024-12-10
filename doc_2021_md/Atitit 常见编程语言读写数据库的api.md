Atitit 常见编程语言读写数据库的api


Php   pdo
php与mysql的连接有三种API接口，分别是：PHP的MySQL扩展 、PHP的mysqli扩展 、PHP数据对象(PDO) 。在这三种方法中，“民间”很多是倾向于使用PDO，因为其不担有跨库（可以和各个数据库连接和处理）的优点，更有读写速度快的特点。 PDO不仅能防止了sql注入问题，同时是面向对象的，所以不管操作还是使用都是挺方便的！今天分享下PHP5中使用PDO操作数据库的方法！
1.PDO简介
PDO(PHP Data Object) 是PHP 5 中加入的东西，是PHP 5新加入的一个重大功能，因为在PHP 5以前的php4/php3都是一堆的数据库扩展来跟各个数据库的连接和处理，什么 php_mysql.dll、php_pgsql.dll、php_mssql.dll、php_sqlite.dll等等。 PHP6中也将默认使用PDO的方式连接

Java jdbctmpltr  
Sprbt jdbctmpltr  mybatis 
Dbutil等

Nodejs  mysql模块

Python pymysql模块

Go语言

import (
	"database/sql"
	"fmt"

	_ "github.com/Go-SQL-Driver/MySQL"
)



Atitit golan conn mysql

