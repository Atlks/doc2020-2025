Atitit worklog s3  2018.3

1. 	3
2. S57	4
3. S54	5
4. 	5
5. S53	6
5.1. 	6
6. S52	8
6.1. 	8
7. S428	9
8. S427	10
8.1. 	10
8.2. 	11
9. S426	12
9.1. 	12
10. S424	13
11. 	13
12. S423	14
12.1. 	15






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

