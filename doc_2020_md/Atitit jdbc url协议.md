Atitit jdbc url协议

JDBC URL 用于标识一个被注册的驱动程序，驱动程序管理器通过这个 URL 选择正确的驱动程序，从而建立到数据库的连接。
　　JDBC URL的标准由三部分组成，各部分间用冒号分隔。

　　①jdbc:<子协议>:<子名称>
　　②协议：JDBC URL中的协议总是jdbc
　　③子协议：子协议用于标识一个数据库驱动程序mysql:
　　④子名称：一种标识数据库的方法。子名称可以依不同的子协议而变化，用子名称的目的是为了定位数据库提供足够的信息
五、几种常用数据库的JDBC URL
　　①对于 Oracle 数据库连接，采用如下形式：
　　jdbc:oracle:thin:@localhost:1521:sid
　　②对于 SQLServer 数据库连接，采用如下形式：
　　jdbc:microsoft:sqlserver//localhost:1433; DatabaseName=sid
　　③对于 MYSQL 数据库连接，采用如下形式：
　　jdbc:mysql://localhost:3306/sid

