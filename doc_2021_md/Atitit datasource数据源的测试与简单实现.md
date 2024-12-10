Atitit datasource数据源的测试与简单实现

构建对象或数据最简单方式是json字符串。。可读性高。。代码行少

本示例使用参数创建完整的 DriverManagerDataSource 类的示例对象，不用再调用方法设置任何属性，关键代码如下：
纯文本复制
String driver = "com.mysql.jdbc.Driver";
String url="jdbc:mysql://lzw:3306/testDatabase";  //创建一个表示数据库路径的字符串
String username = "root";  //创建一个表示数据库用户名的字符串
String password = "111";  //创建一个表示数据库密码的字符串
DriverManagerDataSource driverManagerDataSource = 
  new DriverManagerDataSource(driver,url,username,password);



3

DriverManagerDataSource —標準JDBC DataSource接口的簡單實現，通過bean屬性配置普通的舊JDBC DriverManager，並從每個getConnection調用返回一個新的Connection。
SimpleDriverDataSource —與DriverManagerDataSource相似，不同之處在於它提供直接的Driver用法，這有助於解決在特殊類加載環境（例如OSGi）中使用JDBC DriverManager進行的常規類加載問題。

