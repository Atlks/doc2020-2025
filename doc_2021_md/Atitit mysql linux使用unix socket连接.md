Atitit mysql linux使用unix socket连接


UNIX socket: /var/lib/mysql/mysql.sock

本地主機與127.0.0.1區別
localhot(local) 是不经网卡传输！这点很重要，它不受网络防火墙和网卡相关的的限制。
127.0.0.1 是通过网卡传输，依赖网卡，并受到网络防火墙和网卡相关的限制。
一般设置程序时本地服务用 localhost 是最好的，localhost 不会解析成 IP，也不会占用网卡、网络资源。
有时候用 localhost 可以，但用 127.0.0.1 就不可以的情况就是在于此。猜想 localhost 访问时，系统带的本机当前用户的权限去访问，
而用 IP 的时候，等于本机是通过网络再去访问本机，可能涉及到网络用户的权限。
MySQL連接時主機類型
mysql -h 127.0.0.1的時候，使用TCP / IP連接
mysql -h localhost的時候，是不使用TCP / IP連接的，而使用Unix socket；此時，mysql服務器則認為該客戶端是來自“ localhost”
MySQL手冊5.6.4…..主機值可以是主機名或IP地址，也可以是“ localhost”以表示本地主機。
簡而言之：主要區別是localhost是通過unix domain socket方式來連接，而127.0.0.1則是走的TCP協議方式連接



在Unix上，可以使用兩種不同的方法連接到mysqld服務器：Unix套接字文件（例如 /var/run/mysqld/mysqld.sock），或使用TCP / IP（例如127.0.0.1:3306）。使用Unix套接字文件創建的連接比TCP / IP更快，但是僅當連接到同一台計算機上的服務器時才可以使用。使用Unix套接字文件時，可以跳過連接字符串中的主機名和端口。


步驟3.下載第三方庫
Connector / J驅動程序本身不支持使用Unix域套接字連接到MySQL服務器。要啟用套接字連接，您需要下載第三方庫。有關此限制的更多信息，請參見dev.mysql.com上的使用Unix域套接字連接。

從github.com上的junixsocket存儲庫下載最新版本（例如 junixsocket-dist-2.3.2-bin.tar.gz）。


解壓縮下載的檔案。您需要從lib目錄中將以下文件添加 到DataGrip中的MySQL驅動程序：

junixsocket-mysql-2.3.2.jar

junixsocket-native-common-2.3.2.jar，如果您有自定義架構，請嘗試 junixsocket-native-custom-2.3.2.jar

junixsocket-core-2.3.2.jar
junixsocket-common-2.3.2.jar
步驟4.在DataGrip中配置MySQL驅動程
在“高級”選項卡上，找到socketFactory屬性，雙擊“值”單元格，然後將值更改為 org.newsclub.net.mysql.AFUNIXDatabaseSocketFactory。
