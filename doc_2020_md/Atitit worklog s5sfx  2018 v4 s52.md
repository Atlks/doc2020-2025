Atitit worklog s3  2018.3

1. Yujiyaouppic	2
1.1. S528	2
1.2. S525	4
1.3. S524	5
1.4. S523	7
2. S522	8
3. S521	10
4. S519	11
2. 搜集整理weddav资料	11
5. S518	14
6. S517	16
7. S516	19
8. S515	21
9. S514	24
10. S5a	27
11. 	28
12. S50	29
13. 	30
14. S59	31
15. 	32
16. S58	33
17. 	34
18. S57	35
19. S54	36
20. 	36
21. S53	37
21.1. 	37
22. S52	39
22.1. 	39
23. S428	40
24. S427	41
24.1. 	41
24.2. 	42
25. S426	43
25.1. 	43
26. S424	44
27. 	44
28. S423	45
28.1. 	46

Yujiyaouppic
Chenjyao sujo gf lyosyo


S529
 》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
       elk日志组件应用 监控平台完善 
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

对elk有时候出现no result 问题总了总结，查询资料，需要设置时间，默认时间段会过期导致查不到当前时间段内数据

17服务器部署跨机器日志分析组件elk
青岛-实施李奥运 吴正浩沟通 新的修改
高鑫沟通部署 自动升级组件
Elk界面中文查询资料，找到一个项目下载，安装执行环节
对命令行下java的执行dsl增加了全面的测试，做了解析，构建ast，解释执行。。对最新词法分析语法分析解释执行模式做了全新总结
对多方法做专题化命名法总结提升可读性
 

 ##-----------明日计划tomr plan：
    Elk ui中文问题     监控平台    Es的工具完善   其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
    日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分    内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s529
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------



S528
 》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
       elk日志组件应用 监控平台完善 
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

测试nfs模式，貌似也比较麻烦，决定自定义解决远程文件与本地文件挂载的问题
做协议转换http2loc文件模式，解决了webdav模式下缓存的问题，导致logstack抓取不到最新的日志实时信息
对es logstash内存占用做优化，根据pid分析出进程启动运行参数，找出哪个java进程。。对pid分析运行参数做了总结
优化httplientutil的结构，参考了net java的sdk布局调整位置，增加了大性能情况下的outputstream模式
增加java在命令行shell的直接执行模式，增加了cmd目录语法简析，通用的程序调用单独的方法，不限于main 递归下降法与状态机模式 比较全面的语法分析
增加ftp与自定义embedftp server的模式


 ##-----------明日计划tomr plan：
    Elk ui中文问题     监控平台    Es的工具完善 elk使用
 进程管理  webshell部分完善，还需要增加个web api级别的
其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
    日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分    内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s524
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------


S525
 》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
       elk日志组件应用 监控平台完善 
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩 青岛-实施李奥运 沟通一个部署问题，新版发布版本给测试
本地18服务器实时elk监控组件，部署文件服务，Samba发现比较麻烦，部署了wabdav服务
本地logstash 使用unc和本地映射路径连接log，貌似不是很实时，应该是webdav的缓存造成的，查找资料无果，到时可能需要部署Samba
在18服务器部署logstash  es，进行本地采集这样就没有缓存了，实时采集。
Linux es安装使用过程有些问题解决，记录总结  
大批量小文件压缩问题解决。

##-----------明日计划tomr plan：
         监控平台    Es的工具完善 elk使用
 进程管理  webshell部分完善，还需要增加个web api级别的
其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
    日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分    内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s524
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------


原来打算部署samba服务提供远程文件访问，但是貌似比较复杂，和高鑫沟通了下，部署了个webdav服务，这样就简单很多了

Webdav模式查看日志地址
http://192.168.1.18:1314/webdavapp/webdavurl/home/cnhis/cloudhealth/logs/log.log


Elk  Kibana模式日志查询
http://192.168.1.77:5601/app/kibana#/discover?_g=()&_a=(columns:!(_source),index:'53f0bc20-5fc2-11e8-8ed3-b7b22998739f',interval:auto,query:(language:lucene,query:''),sort:!(_score,desc))

S524
 》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
       elk日志组件应用 监控平台完善 
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩 沟通医嘱校对问题 准备使用存储过程新鞋，现有问题太多
完备elk监控组件的使用。聚集数据乱码问题的解决，多文件聚集文体  
elk监控组件 kibana 多关键词联合查询 查询结果格式可读性提升
测试logstash 日志更新后监控抓取 multiline模式测试
与吴正浩沟通医生站ho移动端统一配置 prop json格式
与高鑫沟通部署elk日志聚合分析查询工具的问题
文档类文件写入日志的纯文本转换功能

##-----------明日计划tomr plan：
         监控平台    Es的工具完善 elk使用
 进程管理  webshell部分完善，还需要增加个web api级别的
其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s524
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------


S523
 》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
       elk日志组件应用 监控平台完善 
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩 沟通医嘱校对问题 准备使用存储过程新鞋，现有问题太多
完备elk日志组件的使用。建立logstash-6.2.4环境聚集数据 使用起来kibana这个Elasticsearch gui工具
Elk不只能能应用在日志分析，还可以应用在文本分析，聚合，全文查询的场合
Elasticsearch 与lucene的多关键词查询dsl api
测试luke7.2 这个lucene gui工具，效果还可
增加ho移动端统一配置 prop json格式


##-----------明日计划tomr plan：
         监控平台    Es的工具完善 elk使用
 进程管理  webshell部分完善，还需要增加个web api级别的
其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s522
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------



/hodoctor/lab1/inspectListByvaa04
/hodoctor/lab1/inspectDetailBylab01
这两个接口是检验信息的接口  
护士站没有
现在想新加过去
有时间了迁移一下
医生站的还要保留哦

Cfg   ....syaodwi neig


S522
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
    监控平台完善    elk日志组件应用
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩马朋沟通一个医嘱校对问题
与高鑫沟通交流接口平台完善优化问题
初步elk日志组件的使用。建立es环境，进一步使用了rest接口。Curl模式测试，java直接连rest接口测试。。Java本地es类库连接，不能接到，貌似类库版本在jdk8，与项目不兼容。
Httpclient方面完善优化了post get的实现，实现了es的测试
Es与lucene的多关键词查询
查询的linq api初步实现



##-----------明日计划tomr plan：
         监控平台    完善测试 elk日志组件应用
Es的工具完善 elk使用
 进程管理  webshell部分完善，还需要增加个web api级别的
其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s522
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------


S521
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
    监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

监控平台自动升级功能增加可选路径模式
Webdav的应用（涉及到文件新增复制移动删除，搜索，上传下载编辑等功能）
搜集ssh接口的实现与应用
搜集elk日志组件的使用。
Es的环境建立与初步使用
Httpclient方面做了put方面的完善 ，优化了post的实现



##-----------明日计划tomr plan：
         监控平台    完善测试
Es的工具完善 elk使用
 进程管理  webshell部分完善，还需要增加个web api级别的
其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s5g
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------


S519
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩史国涛石仕成丁宝 李佳栋沟通交流ho移动端现场部署问题的反馈
搜集整理weddav资料 



##-----------明日计划tomr plan：
     护士站后端功能跟进调整   监控平台    完善测试
文件上传下载 功能完善了http  ftp 级别 双通道，预计增加个webdav接口
文件搜索功能，通过web shell ，ftp实现，还需要增加个web api
运行程序 webshell 与http api 均已完善 需要增加直接ssh通道
文件的管理与操作 webshell  与ftp实现，还需要实现各http web api接口的，测试下webdav接口是否可以用用在这块
文件编辑   shell 部分不需要，ftp和web api已经完善。。预计要增加个webdav接口
性能监控 webapi可视化部分与web shell部分均已完善
进程管理  webshell部分完善，还需要增加个web api级别的，增加ssh通道模式的
其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s5g
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------



S518
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩史国涛石仕成丁宝 李佳栋沟通交流ho移动端现场部署问题的反馈
监控平台完善linux兼容版本 ，完善了iostat 磁盘监控占用时间百分比显示
增强了cpu监控的可视化历史曲线   
增强监控平台可读性，拆分了内存监控与cpu监控部分代码按照平台
增强shell执行后结果可读性 shell执行后结果结构化返回修改，改为由前段join显示格式化
增加了自定义通用异常用来包装exception，增加了调试信息附加，增加了自定义抛出异常api，带来更好的跨平台一致性
增加测试增加sh文件权限执行，这方面shell工作
监控全面增加了junit单元测试
针对shell命令在编程环境下返回的显示问题全面做了总结
对js 和java的json数组join api统一化，与guava的模式为主
总结功能实现的三个层次  shell级别 http web  api级别  公用协议。。
对目录浏览功能三个层次实现全部实现
对解压与压缩功能三个层次 实现了shell级别和初步 web api
ho移动端胆红素和疼痛等级字段不显示问题的修正工作，与吴正浩石国涛沟通交流
 



##-----------明日计划tomr plan：
     护士站后端功能跟进调整   监控平台    完善测试
文件上传下载 功能完善了http  ftp 级别 双通道，预计增加个webdav接口
文件搜索功能，通过web shell ，ftp实现，还需要增加个web api
运行程序 webshell 与http api 均已完善
文件的管理与操作 webshell  与ftp实现，还需要实现各http web api接口的，测试下webdav接口是否可以用用在这块
文件编辑   shell 部分不需要，ftp和web api已经完善。。预计要增加个webdav接口
性能监控 webapi可视化部分与web shell部分均已完善
进程管理  webshell部分完善，还需要增加个web api级别的
其他，预计测试集成下SNMP协议，看可否应用起来

##-------其他未尽事宜Backlog 
 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s5g
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------


S517
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩史国涛石仕成丁宝 李佳栋沟通交流ho移动端线程部署问题的反馈
Ho移动端分为通用版和特殊版分支，方便管理。
监控平台与高鑫沟通部署新版本，测试cpu 内存监控 完善linux兼容版本    
增加了稳定性，隔离不同子功能，防止相互影响，
完善总结命令行 linux服务器负载cpu 内存命令api shell top的特殊使用在java环境下
Zip压缩包模块完善文件列表处理功能 在linux下的解压路径问题兼容
shell执行后结果结构化返回修改
测试sh文件需要增加了权限，才可执行，增加了这方面工作
磁盘io监控完善与独立可视化监控
Java与js异常转换 跨语言异常转换
Linux不同版本下的top返回结果不同，重新根据18服务器的做了解析，未来可能需要兼容多个版本。




##-----------明日计划tomr plan：
     护士站后端功能跟进调整   shell执行后结果结构化返回修改完善，格式化放在js端进行，，自定义异常与异常抛出api，替换语言级别的api，更好的跨平台一致性，， 监控平台进一步完善    完善测试
##-------其他未尽事宜Backlog 
 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s5g
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------



S516
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩史国涛石仕成丁宝 李佳栋李佳栋沟通交流ho移动端线程部署问题的反馈
监控平台cpu 内存监控 完善linux与win兼容版本    
磁盘io监控完善与独立可视化监控
完善总结命令行 服务器负载cpu 内存命令api shell
测试Sigar数据收集组件。它用来从许多平台收集系统和处理信息。。但是因为使用了平台相关的dll so库，所以没有最终使用。。使用基于cli的api更加易用
界面ui结构调整完善
对异常处理分类处理与做了类树形链形分析工作。。
Zip压缩包模块完善文件列表处理功能
Csv组件增加tab风格解析功能
Rest接口增加了同一入口风格




##-----------明日计划tomr plan：
     护士站后端功能跟进调整       监控平台进一步完善   
##-------其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s5f
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------




S515
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩史国涛石仕成丁宝 李佳栋李佳栋沟通交流ho移动端线程部署问题的反馈
完善保存危重记录的单元测试，对ide返回数据，json转csv，pretty模式增加。方便了查看返回数据在ide对照
 解决编码乱码的检测与纠正  设置乱码纠正与检测 ，
 对危重记录保存于单元测试  数据结果查看 做了完善文档记录，结果全部可以在ide里面查看了，提升用户体验
对17服务器的ho后端部署增加了自实现ftpsrever，方便部署维护，bs cs俩种模式完善
把监控平台的部分大部分功能同步到17服务器
石国涛反馈保存有个字段貌似有点错位，分析，修正，打包，发布
监控平台小型化，去除了不需要的jar，减少打包体积，对maven打包时候增加容错，忽略测试代码的编译错误
    
##-----------明日计划tomr plan：
     护士站后端功能跟进调整       监控平台进一步完善   资源监控的cpu 内存占用在linux返回的分析解析

##-------其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s5f
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------




S514
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与吴正浩史国涛石仕成丁宝 李佳栋李佳栋沟通交流ho移动端线程部署问题的反馈
完善上传zip更新包后的linux与window路径兼容问题以及发布测试
完善监控平台执行更新脚本的路径问题，兼容linxu与windows的shell执行
完善平台的用户体验，增加美化按钮与loading模式，增加菜单完善
 增加自定义异常返回时候的附加信息，组合模式代替了继承模式  用来反馈解压信息 ，路径信息等
与史国涛沟通一个编码乱码问题，初步分析与解决方案，总结二进制编码问题 重新与吴正浩同步打包
初步设置乱码纠正与检测 增加常用字表收集，
升级包结构调整与测试，方便执行shell，找到默认shell
对url参数传递提升可读性，总结搜集了更好的文本结构方式
对危重记录保存于单元测试  数据结果查看 做了完善文档记录
    
##-----------明日计划tomr plan：
     护士站后端功能跟进调整      日志监控模块进一步完善   资源监控的cpu 内存占用在linux返回的分析解析

##-------其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s5a
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------





S5a
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

增加上传zip更新包文件后后解压，以及执行更新脚本。。完善界面反馈
与实施工程师 丁宝沟通项目部署问题  
 与高鑫沟通更新升级包结构与增加脚本功能
增加zip格式文件更新包修改功能 更新包修改功能使用ant 和common compare都无法直接解决，通过调用cli接口rar解决。
增加zip包遍历时候的回调，用来反馈解压信息
更新打包工具版本更新，baseline baeline core，按照时间打包等功能
和高鑫沟通不同版本差异打包增量打包的问题，解决完整打包体积过大
    
##-----------明日计划tomr plan：
     护士站后端功能跟进调整      日志监控模块进一步完善   资源监控的cpu 内存占用在linux返回的分析解析

##-------其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s5a
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------





S50
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与史国涛沟通联调反馈护士站后端功能跟进微调  
 与吴征浩高鑫沟通在17服务器部署移动护士站 医生站最新修改
Hislog项目 增加ftp文件第三方直接读取功能 无需中转文件apache common net模式
与高鑫沟通交流自动升级
初步设计自动升级cli gui模式。先实现细节专家模式，然后要实现傻瓜化一建操作模式。。组合集成
百度可视化事件河流event river的初步测试，适用于趋势类时间轴的图表
增加ftp独立配置项目\ftpserverati 简化项目部署与稳定性
对zip解压增加与改进，解压到指定目录功能与解压到当前目录功能 ant类库使用 
   
##-----------明日计划tomr plan：
     护士站后端功能跟进调整  整合解压 sql执行与shell执行功能
   日志监控模块进一步完善   资源监控的cpu 内存占用在linux返回的分析解析

##-------其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s50
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------




S59
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与史国涛沟通联调反馈护士站后端功能跟进微调 危重记录保存 增加了几个字段保存 
与胡朝进沟通交流 监控平台集成入受权管理系统里面。
根据吴征浩的要求把移动护士站的病例文件列表功能也同步到医生站，说医生站app也要使用。。
增加sql语句执行功能，与sql脚本文件执行功能
全面对监控平台的首页h5部分做了移动端兼容测试与美化使用bootstrap  加了部分字体模式图标 面板布局优化   
第三方远程文件操作与编辑基础功能实现 需要集成到建面预计要集成支持ftp ssh nfs等网络协议
对远程文件操作端口做了容错冗余处理增加稳定性
对csv格式结合json格式做了增强，增加了head与解析器用来做配置文件解析
对所有远程常用远程文件协议做了文档总结
  
##-----------明日计划tomr plan：
     护士站后端功能跟进调整
   日志监控模块进一步完善   资源监控的cpu 内存占用在linux返回的分析解析

##-------其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s59
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------



S58
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：

与护士站后端功能跟进微调 
 监控平台增加cpu 内存  io使用监控的可视化界面
搜集报表类库，选型了百度echarts 跨平台类库  对选型流程与结果也做了总结  
监控平台增加了web使用浏览器打开ftp协议的界面与测试。
监控平台可视化功能图表功能继续搜集完善
对gui接口操作功能做了一些搜集整理
Web Js访问剪贴板兼容性貌似有问题，增加了本地代理访问剪贴板，怎加了命令行接口跨语言剪贴板功能
 
##-----------明日计划tomr plan：
     护士站后端功能跟进调整
   日志监控模块进一步完善   资源监控的cpu 内存占用在linux返回的分析解析

##-------其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s58
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------



S57
》》工作日志笔记记录日报《《

##-------------------------当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 

##--------------------今日工作today：
与熊跃龙吴征浩就-危重记录自定义字段获取联调，更具反馈与修正沟通吴正浩 
 监控平台增加本地代理的文件 ，方便web调用 绝对路径选择器等工具
 监控平台完善内嵌式ftp server集成与测试   文件上传下载与一些移动复制操作方便实施  以及目录浏览
与行政沟通交流 协助解决一些  spring cache的问题  
 对可读性提升对减少代码行数模式Iniblock,lambda，builder模式一一做了总结
监控平台可视化功能初步搜集
 
##-----------明日计划tomr plan：
     护士站后端功能跟进调整
   日志监控模块进一步完善  

##-------其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s57
mybatis缓存集成redis的稳定性性能增强

-------------END(完)----------

S54
工作日志笔记记录日报
###当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 
##今日工作today：

与高瑜沟通交流  通过hodebug 住院护士站-选择病人-病人护理记录-新增记录
护理记录单-危重记录自定义字段获取 高鑫 通过hodebug  
三测单录入-危重记录(自定义)-获取、提交、与吴正浩沟通完善 接口ok 与吴正浩高鑫 高瑜 熊跃龙(沟通三测单录入-危重记录(自定义)-获取 的sql，完善然后与吴正浩联调接口
与吴正浩联调 反馈医嘱停用单个可以，批量貌似有点问题，修正，在此联调通过
提升可读性，做了可读性优化尽可能
重新部署联调版本的web服务器，方便联调不影响本地修正分离
对可读性提升  流畅接口做了总结收集整理资料

  ##明日计划tomr plan：
     护士站后端功能跟进调整
   日志监控模块进一步完善  
   ##其他未尽事宜Backlog 
 ftp文件管理
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s52
mybatis缓存集成redis的稳定性性能增强


S53
工作日志笔记记录日报
###当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 
##今日工作today：

监控平台可视化部分功能总结
三测单录入-危重记录(自定义)-获取、提交、与吴正浩沟通完善 接口ok
与吴正浩高鑫 高瑜沟通三测单录入-危重记录(自定义)-获取 的sql
移动护士站后端功能病历文件类型接口 ok
 进一步完善mybatis测试，按照是否依赖xml和mybtis类库拆分优化俩个结构
对mybatis查询接口结果映射问题，解决花了点时间，预计要把batis常见问题主题总结
 Tomcat报了一个jar解压错误，做了jar的遍历测试，使用本地同步器手动同步，jar损坏原因未知
对request和mybatis参数对应自动填入做了封装，减少重复代码，提升可读性
监控平台常用webshell命令收集，win和linux双系统，准备做模板化 ，搜集了ahk截屏命令
  ##明日计划tomr plan：
-危重记录获取功能接口  监控平台文件搜索的测试与完善 护士站后端功能跟进调整
   日志监控模块  ftp文件管理
    ##其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s52
mybatis缓存集成redis的稳定性性能增强



S52
工作日志笔记记录日报
###当前工作curr：
   移动护士站 监控平台完善  
 分析原因解决问题 优化性能 功能 与其他事项 
##今日工作today：

监控平台上传下载功能
监控平台集成webshell测试，貌似部分不完善，与自己实现webshell。。Webshell部分比较多，一一解决问题做了文档总结
文件搜索功能完善
测试webshell 下的文件搜索 性能检测 压缩解压 目录浏览功能，记录测试数据与用例 
移动护士站医嘱停用功能与吴正浩沟通交流修改联调
 和倪俊 黄信沟通 移动护士站后端功能情况 与高鑫沟通交流日志平台的部署与测试  
 
  ##明日计划tomr plan：
监控平台文件搜索的测试与完善 护士站后端功能跟进调整
   日志监控模块  ftp文件管理
    ##其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）可视化
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s52
mybatis缓存集成redis的稳定性性能增强


S428
工作日志笔记记录日报
###当前工作curr：
  性能模块修改 监控平台（包括在线文本文件编辑器，在线日志console控制台，在线目录资料浏览器等）   mybatis缓存集成redis的稳定性性能增强
 分析原因解决问题 优化性能 功能 与其他事项 
##今日工作today：

日志平台的war打包，测试使用zip 和eclipse打包都有点问题，使用maven打包功能调整了不少参数，总结了。。更好的实现了打包war，直接打包在tomcat平台下部署
监控平台部分功能 文件编辑器增加编码选择
增加目录资源浏览器 前后段与测试
初步增加文件搜索功能
在线目录资料浏览器后端   
Elfinder web文件管理器测试集成，有错误解决，使用Quercus 环境有问题 与独立环境测试，不能指定起始目录
和黄信沟通 移动护士站后端功能 三测单录入-危重记录(自定义)-获取、提交 的功能 
 与高鑫沟通交流日志平台的部署与测试 与其他人员的沟通增加项目日志配置动态加载片段
对其他文件编辑器功能大搜集，总结，提取对我们有用的功能点集合路线图。。

  ##明日计划tomr plan：
监控平台文件搜索的测试与完善   日志监控模块 
监控平台Web Shell模块的前后段集成   护士站后端功能跟进调整
##其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。  s428



S427
工作日志笔记记录日报
###当前工作curr：
  性能模块修改 监控平台（包括在线文本文件编辑器，在线日志console控制台，在线目录资料浏览器等）   mybatis缓存集成redis的稳定性性能增强
 分析原因解决问题 优化性能 功能 与其他事项 
##今日工作today：

监控平台部分功能
在线文本文件编辑器，前后端与测试
在线日志console控制台，前后端与测试
在线目录资料浏览器后端   
Elfinder web文件管理器看起来功能蛮多还可，搜集资料与测试，准备集成到监控平台去
和余杰沟通 移动护士站后端补丁应用与更新  
 集成测试可以进行方便的 Log4g日志动态加载功能与调整了
监控平台Web Shell执行环境后端部分

  ##明日计划tomr plan：
  日志监控模块 监控平台Web Shell模块的前后段集成   护士站后端功能跟进调整
##其他未尽事宜Backlog 
Java与js异常转换 在线文本文件编辑器的语法着色  保存时候语法检查增强  日志console控制台语法着色 增强可读性    Web Shell语法着色，自动提示  报警模块
完善监控平台 可视化部分准备  系统资源部分集成（cpu占用，io，内存，网络等）
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。实现常见的一些字段函数 s427




S426
工作日志笔记记录日报
###当前工作curr：
  性能模块修改  医保接口  mybatis缓存集成redis的稳定性性能增强
 分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：

内存数据库资料收集
  和 吴正浩 黄信 于杰 马朋 沟通交流移动护士站后端医嘱批量 校对、发送 后 药物剂量频次不对的问题
和吴正浩沟通联调修改 移动护士站后端医嘱批量发送 后 的问题  
调试工具Tomcat 过滤器日志顺便移植到移动护士站后端，方便记录传递参数
与胡超净沟通，建立了日志检测的整体环境
调试工具 Log4g日志动态加载功能，查询资料，测试了几种方式，最终确定一种生效，文档记录总结，方便了及时调整日志级别 方便分析在线问题
在线日志配置文件编辑器查看器大概构思设计 

  ##明日计划tomr plan：
  日志监控模块   护士站后端功能跟进调整
##其他未尽事宜Backlog 
 内存数据库 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。实现常见的一些字段函数
分区工具获取与分析索引ddl 根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s424


S424
工作日志笔记记录日报
###当前工作curr：
  性能模块修改  医保接口  mybatis缓存集成redis的稳定性性能增强
 分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
协助李雨淋 王增歧 解决缓存应用中的问题
 和胡朝进 张超清 李雨淋 沟通交流spring redis缓存的应用
 和 吴正浩 黄信 沟通交流移动护士站后端护士站巡视病人列表功能
增加了缓存手动清除的api 优化了一些小问题 协助 王增歧合并到common里面去
和马朋 高鑫沟通护士站一些问题与权限

  ##明日计划tomr plan：
测试打版本 参数调优  计划把库存表放入redis 以及操作api    护士站后端功能跟进调整
##其他未尽事宜Backlog 
 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。实现常见的一些字段函数
分区工具获取与分析索引ddl 根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s424


S423
工作日志笔记记录日报
###当前工作curr：
  性能模块修改  医保接口  mybatis缓存集成redis的稳定性性能增强
 分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
Spring redis缓存读写稳定性增强 增加了timeout机制，读取超时后略过
 增加了timeout 连续三次读写错误重置状态功能
Key可读性增强  val可读性增加 增加了监控键值方便调试查看
和王增岐 马朋 韩磊宏李雨淋 沟通交流spring redis缓存的应用
结构调整优化可读性
 配置化增强  连接测试器，增加了若干配置参数
增加了单独设置key的过期时间功能 与测试
和张家乐  吴正浩 黄信 沟通交流移动护士站后端护士站巡视病人列表功能
缓存结构优化为稳定性 性能层 功能层 ，对性能俩个检测器也做了拆分优化 

  ##明日计划tomr plan：
测试打版本 参数调优   key生成多参模式的json序列化失败后的 参数类型+hascode代替

##其他未尽事宜Backlog 
 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。实现常见的一些字段函数
分区工具获取与分析索引ddl 根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s420

