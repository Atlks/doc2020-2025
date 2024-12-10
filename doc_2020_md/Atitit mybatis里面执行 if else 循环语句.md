Atitit mybatis里面执行 if else 循环语句

不能直接执行，，mybatis sql不支持匿名块 必须在其他对象中使用;

DROP PROCEDURE IF 	EXISTS `tt`;
CREATE PROCEDURE `tt` ( ) BEGIN#Routine body goes here...
	
	SET @i = 0;
	IF	@i > 1 THEN
			SELECT			'gtr';
		ELSE
 			SELECT			'lit';
		
	END IF;
	
END;
CALL tt ( );

MYSQL不支持匿名块，存储过程语句只能放在存储过程中执行。


PLSQL 是Oracle公司在SQL基础上进行扩展而成的一种过程语言。 PLSQL提供了典型的高级语言特
性，包括封装，例外处理机制，信息隐藏，面向对象等；并把最新的编程思想带到了数据库服务器和工具
集中。

定义格式
PLSQL是一种类PASCAL语言，每一段程序都是由Block 组成的，其中BEGIN--END--程序块是不可或缺的；
1

[DECLARE]
--变量声明
BEGIN
--程序语句
[EXCEPTION]
--异常处理
END;
————————————————
探究：MySQL是否存在像Oracle一样的匿名块用法？MySQL如何使用流程语句？ - 牛尚小的博客 - CSDN博客.html
