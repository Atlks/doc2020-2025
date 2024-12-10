Atitit common insert数据接口


注意问题
@注解  分离http控制参数与数据参数问题
多余参数问题，参照表结构过滤掉
固定createtime等字段默认值问题，可以是cfg code搞定
语句使用set模式可读性更高


案例  addApi?@data=table&f1=1&f2=2&data=xxx


Atitit insert插入数据

目录
1.1. INSERT INTO SET这种方式可读性更好	1
1.1.1. 方式4、INSERT INTO 表名 SET 列名1 = 列值1,列名2=列值2,...;（博友提供，感谢）	1
1.2. Merge融合插入	1
1.3. 批量插入 INSERT INTO SELECT 语句	1
1.4. SELECT ... INTO 语句	2

Atitit insert sql种类

目录
1. Insert的种类	1
2. 语法原理	1
3. 现状	1
3.1. Oracle语法	2
4. Mysql的实现	2
4.1. mysql的replace into命令	3
