Atitit arch design context软件架构设计的内容

目录
1. 考虑到架构设计原则	2
1.1. 开发效率  稳定性 可靠些等 性能	2
1.2. 简单原则则	2
1.3. 配置化 vs 开发	2
2. 云平台vs自建	2
2.1. Rds mysql	2
3. 架构灵活性内容	3
3.1. 语言和数据库 基础设施	3
3.2. 类库	3
3.3. 开发模式 层次 tod等	3
4. 开发语言选项 4gl优先	3
5. 数据库选择sql erver vs mysql	3
6. 类库选择 简单优先	3
7. 部署os win vs linux	4
8. 架构模式   单体 vs 分布式	4
8.1. 模块化  井字模式	4
8.2. 通用化模块 vs 业务相关模块	4
8.3. 分层层次数 双层 》 三层 》多层	4
8.4. 免编译免部署 配置化	4
8.5. Db oritd模式优先	4
8.6. Table oritd vs java oritd	4
9. Ati的架构演化路线	4
9.1. 淘宝的架构演化路劲	5

考虑到架构设计原则
开发效率  稳定性 可靠些等 性能
简单原则则



配置化 vs 开发
Cs vs bs架构
单体架构  分布式架构（msa soa）
云平台vs自建
Rds mysql

架构灵活性内容
语言和数据库 基础设施
类库
开发模式 层次 tod等
开发语言选项 4gl优先
开发效率 sql 》 script 》 java
综合使用，嵌入模式可以

数据库选择sql erver vs mysql

类库选择 简单优先
Springboot
Websocket  workerman 比 Swoole 简单
Orm mybatis jpa hb 
Ngnix vs dobbo》 springcloud
Json、序列化 

部署os win vs linux
架构模式   单体 vs 分布式
Soa架构  msa微服务架构

实现模式  ws rest 

应该单体优先中小项目

模块化  井字模式
通用化模块 vs 业务相关模块
通用库表查询 操作
分层层次数 双层 》 三层 》多层
免编译免部署 配置化
Db oritd模式优先
Table oritd vs java oritd

Ati的架构演化路线
架构演化路劲
云平台 rdmysql 
数据库服务器分离
Cache 内存表  零食表缓冲 redis
Sql调优 replace > insert dulip update,,insert delay  ingorn
负载均衡 nginux Lvs 负载均衡多个nginx ，Dns轮询负载均很
Db 读写分里
分区
按照用户 地域 时间分库  (不要按照业务分库，麻烦
Nosql 技术 mongodb es等

淘宝的架构演化路劲
数据库服务器分离
Cache 内存表  零食表缓冲 redis
负载均衡 nginux
Db 读写分里
分区
业务分库
Lvs 负载均衡多个nginx
Dns轮询负载均很
Nosql 技术 mongodb es等
应用拆分》》微服务》》esb企业总线》》容器化》》云平台



