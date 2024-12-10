Api 接口规划与实现

需求  2hz的注单数据同步到newec，并做数据格式转换


简单原则 最小化

Pull vs push模式选型
Pull只需要对接数据库自带提供的的socket远程接口即可，在2hz端无需做任何调整。更加简便。。可以增加一个独立的socket转rest接口。。Timer定时拉取

如果使用推送模式，则需要2hz调整代码，较为繁琐

实现语言 php5.6--7 
语言特性5.6,，兼容5.6以及php7

涉及api与类库
Timer 使用swoole workerman ，也可单独挂载在os提供的定时任务中运行，更灵活性
数据库读取使用pdo api
Httpclient使用编程语言内部自带api

微服务化容器化
包括web rest服务提供全部一体化内嵌。。无需额外的web容器部署。可直接命令行一行启动运行多个端口实例


