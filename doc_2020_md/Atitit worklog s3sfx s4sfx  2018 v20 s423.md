Atitit worklog s3  2018.3

1.2. 	2
1.3. S419	3
1.4. 	3
1.5. S418	4
1.6. 	5
1.7. S417	6
1.8. S416	7
1.9. 	7
1.10. 1.1.s4c	7
1.11. 	8
1.12. 1.1.s4b	9
1.13. s49	12
1.14. S48	13
1.15. S44	14
1.16. S43	15
1.17. s43	16
1.18. S328	20
1.19. 2018.3.26 工作日志笔记记录日报	21
1.20. 2018.3.6 工作日志笔记记录	22
1.21. 当前工作：	22
3. postgresql日志暴增的解决 今日工作：	23
3. postgresql日志暴增的解决第二版，与耿帅沟通测试	23
1.22. 当前工作：	24
今日工作：	24
1.23. #当前工作：	25
#今日工作：	25
6. 移动端的兼容支持  移动端测试	26
1.24. #明日计划： #其他未尽事宜Backlog	26
1.25. #当前工作：	26
#今日工作：	26
1.26. #明日计划：	26
1.27.  #其他未尽事宜Backlog	27
1.28. 2018.3.13  工作日志笔记记录日报	27
1.29. #当前工作：	27
#今日工作：	27
1.30. #明日计划：	28
1.31. #其他未尽事宜Backlog	28
1.32. #当前工作：	28
#今日工作：	28
1.33. #明日计划：	29
1.34. #其他未尽事宜Backlog	29
1.35. #当前工作：	29
#今日工作：	29
1.36. #明日计划：	30
1.37. #其他未尽事宜Backlog	30
1.38. #当前工作：	30
#今日工作：	30
1.39. #明日计划：	31
1.40. #其他未尽事宜Backlog	31
1.41. #当前工作：	32
#今日工作：	32
1.42. #明日计划：	33
1.43. #其他未尽事宜Backlog	33
1.44. 2018.3.23 工作日志笔记记录日报	36



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


S420
工作日志笔记记录日报
###当前工作curr：
门诊问题修改 性能模块修改  成都医保接口 合理用药
 分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
Spring redis缓存读写稳定性异常处理，去报缓存失效异常情况下的正常使用
 Key 生成器稳定性异常处理，增加了备用的可以生成随机字符key模式 
Redis断开后的异常处理。与测试。。确保断开后也无异常报错。。
经过测试，redis断开后重试时间较长。增加连接测试器，定时测试连接，切换状态 要不要走缓存。
远程redis与本地redis测试，使用本地redis减少远程网络交互，本地redis远程redis配置文件分离，独立，经过与肖鹏沟通，发现公用一个配置可能互相影响登录
 缓存key生成的完善，确保正确性，增加了 类名方法名参数签名模式。。
缓存方面的最佳实践和问题总结
 redis配置读取与优化   测试结果对比减少了30%的数据库连接
缓存可用性与性能提升  定时检测redis 与切换状态
增加  Set 异步化 与线程池模式与测试  与线程池预热

  ##明日计划tomr plan：
测试打版本 参数调优   key生成多参模式的json序列化失败后的 参数类型+hascode代替

##其他未尽事宜Backlog 
 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。实现常见的一些字段函数
分区工具获取与分析索引ddl 根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s420


S419 
工作日志笔记记录日报
###当前工作curr：
门诊问题修改 性能模块修改  成都医保接口 合理用药
 分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
 接入redis 选择db管理。然后还有可视化工具，使用中的线程池模式，但是貌似有问题，不好升级版本，使用theardlocal模式解决
Mybatis集成redis 测试，方便缓存监控与管理
mybais默认全部select走缓存 这个默认有问题，新加白名单的拦截器，只许白名单内走缓存，以便减少稳定性风险
默认namespace up del操作清空缓存，做了拦截不让他自动清空，不让缓存失效。使用时间到期清空模式
 只有读取缓存，不能顺便更新缓存问题的解决，可能是因为业务spring没有自动事务提交，单元测试关闭连接后才刷新缓存，所以增加手动更新缓存功能。。
 经过一把性能测试，但是好像好像是通过网络连接的不是很快，所以又给mybatis增加了一个本地的guava缓存模式。增加了本地缓存查看
对spring cache也全面集成redis  默认的spring缓存也存在管理不方便问题，工具缺乏，也接入redis集成，缓存全面走redis
spring默认的缓存key生成的不便于调试，经过一番资料查询，资料很少，增加了自己的一个key生成器。
正对缓存不能生效问题排查解决与做了文档总结与
缓存方面的最佳实践和问题总结
  ##明日计划tomr plan：
测试打版本 redis配置读取与优化 参数调优  增加redis缓存失效与断开后后的测试与稳定性  put get全面增加try catch  优化安全性。。
 
##其他未尽事宜Backlog 
 做列表缓存集合的join连接 列表缓存 常见的聚合操作完善。实现常见的一些字段函数
分区工具获取与分析索引ddl 根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s419



S418
工作日志笔记记录日报
###当前工作curr：
门诊问题修改 性能模块修改  成都医保接口 合理用药
 分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
 把性能提升分支的代码不断的同步到主版，不断测试验证功能性确保稳定性
修正昨天发现的医嘱计价和医嘱抄送记录不能显示出来的问题
测试库存，发现spring mybatis缓存读取对库存读取又影响，把库存部分配置为强制不读取缓存
 全面进行缓存与测试 提升性能。。 ，减少了数据库读取与交互
对库存部分，计价部分做了文档记录。。
增加测试工具 方便维护人员进行性能测试。。
增加mybatis与redis集成
  ##明日计划tomr plan：
测试打版本 做列表缓存集合的join连接
 
##其他未尽事宜Backlog 
  列表缓存 常见的聚合操作完善。实现常见的一些字段函数
分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s418

要不这样把，我们先上spring dao层的数据缓存打版本，这块改动最小 ，， 然后mybatis缓存打一个版本，然后redis 一类缓存 guava模式自定义缓存打版本。。然后再多线程这个，这块改动较多，影响较大。循序渐进的增进。限制影响范围，有情况也方便缩小范围 方便处理，。你看这样怎么样？




S417
工作日志笔记记录日报
###当前工作curr：
门诊问题修改 性能模块修改  成都医保接口 合理用药
 分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
医嘱发送方面 多线程cpu核数增加设置俩个线程池各自占用的cpu核心数
把性能提升分支的代码不断的同步到主版，不断测试验证功能性确保稳定性
增加了guava模式的cache 缓存
增加了spring 下的cache 模式，查阅资料接入系统。。
各种cache缓存模式的文档总结与集成测试
与马朋沟通交流医嘱方面一些业务问题。。
全面进行缓存与测试 提升性能。。 ，减少了数据库读取与交互
把保存医嘱功能也功能流程图完善 方便调整顺序与优先级提升性能。
除了增加map类型的缓存，还增加了ListCache ，可以提供更加丰富类型的数据，
做列表缓存做了增强，增加了做了过滤和排序 预计方便执行一些缓存操作
做列表缓存做了初步的groupby 分组聚合
 ##明日计划tomr plan：
测试打版本 做列表缓存集合的join连接
 
##其他未尽事宜Backlog 
  列表缓存 常见的聚合操作完善。实现常见的一些字段函数
分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s417



S416
工作日志笔记记录日报
###当前工作curr：
门诊问题修改 性能模块修改  成都医保接口 合理用药
 分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
测试不同cpu核数设置下的性能表现
把性能提升分支的代码不断的同步到主版，不断测试验证功能性确保稳定性
与马朋沟通交流医嘱方面一些业务问题。。
Jvisual工具查看方法线程时间占用有些问题，增加了jprofile时间分析。。
对发送与保存医嘱方面的读取参数部分增加了 本地内存缓存 ，减少了数据库读取与交互
增加了mybatis缓存与测试 提升性能。。 ，减少了数据库读取与交互
功能流程图完善 方便调整顺序与优先级提升性能。
 ##明日计划tomr plan：
测试打版本
 
##其他未尽事宜Backlog  s416
  本地表缓存   


分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s4c

1.1.s4c
工作日志笔记记录日报
###当前工作curr：
门诊问题修改 性能模块修改  成都医保接口
ho移动护士后台端功能完善 
分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
做url模式的测试
把性能提升分支的代码不断的同步到主版，不断测试验证功能性确保稳定性
与马朋沟通交流医嘱方面一些业务问题。。
药品禁售 库库存检查 药品过期等流水线模式多线程子线程异常优化
对医嘱发送 增加了内部线程池，防止子线程数过多造成性能下降 测试不同线程池子任务数量时候的性能表现
增加了子任务优先级模式 不重要的子任务设置较低优先级 ，对不重要子任务单独设置低优先级线程池
对高优先级子任务也单独建立线程池 分开设置
将大流程且分为小流程，测试效果有提升，但cpu占用过多，可能是线程过多造成频繁切换，增加线程池
增加了线程池测试效果明显，提升一个数量级，原来100线程8s，现在可以几百毫秒了
使用jvisual线程分析工具进行了详细的方法线程级别分析，比起时间日志模式要方便，收集时间更加方便。。
##明日计划tomr plan：
 多线程流水线缓存继续增加
 
##其他未尽事宜Backlog
 Mybatis缓存接入 本地内存表缓存 本地表缓存 本地pgsql表作为缓存 分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s4c

今天改动了下，加了线程池，把一个线程同步处理的过程，分拆成多个子任务， 效果可以，但是代码改动较多，线程添加过多也切换太频繁，比较消耗cpu。还需要想办法简化下


1.1.s4b
工作日志笔记记录日报
###当前工作curr：
门诊问题修改 性能模块修改 ho移动护士后台端功能完善 
分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
做url模式的测试
把性能提升分支的代码不断的同步到主版，不断测试验证功能性确保稳定性
与马朋沟通交流医嘱方面一些业务问题。。
药品禁售 库库存检查 药品过期等流水线模式多线程子线程异常优化
 增加了内部线程池，防止子线程数过多造成性能下降 测试不同线程池子任务数量时候的性能表现
增加了子任务优先级模式 不重要的子任务设置较低优先级
##明日计划tomr plan：
url模式多线程
 
##其他未尽事宜Backlog
 缓存接入 本地内存表缓存 本地表sqlite缓存 本地pgsql表作为缓存 分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s412

今天改动了下，加了线程池，把一个线程同步处理的过程，分拆成多个子任务， 效果可以，但是代码改动较多，线程添加过多也切换太频繁，比较消耗cpu。还需要想办法简化下








1.1.s4a
工作日志笔记记录日报
###当前工作curr：
门诊分区支持与测试 性能模块修改 ho移动护士后台端功能完善 
分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
发送医嘱时候继续分析，增加了细化了步骤时间点收集，又找到几个较慢的步骤
对其进行futuretask模式改造与测试3. 
查找性能提升流水线模式的另外一个实现ForkJoinTask模式资料，以及java中的实现  ，需要做一些改动，改动较小 测试完善，不知为什么在spring模式下貌似有ForkJoinTask模式有线程问题，对改动的几个回退到futuretask，测试通过。
一共大概改动了二十来处，不断的优化测试，缩减时间。。
单元测试通过后，使用web模式综合测试，发现稍有问题，可能是哪块修改过多，新开一个性能提升分支，主版暂时恢复原版，同步了部分修改，一步步测试合并


##明日计划tomr plan：
  缓存接入
##其他未尽事宜Backlog
mybatis缓存接入 获取表格ddl生成分区模式ddl
分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s40









1.2.s40
工作日志笔记记录日报
###当前工作curr：
门诊分区支持与测试 性能模块修改 ho移动护士后台端功能完善
增加眼别，院方提供眼别信息；核对基础信息 
分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
6.与马朋沟通 交流发送医嘱时候的问题
7.对表的操作 实现内存缓存模式功能 经过测试效果显著，但改动较大
8.查找性能提升模式流水线模式资料，以及java中的实现futuretask模式，效果也可，需要做一些改动，改动较小
9.详细拆分mybatis中大sql为单条小语句，单独分析时间，定位到update批量更新较慢，使用with模式测试对性能么有提升，只是提升了可读性
10.将建立临时表和插入临时表语句分开，建立临时表单独提前走futuretask模式
11. 语句拆分以后，临时表转换为物理表还是非常有用的，方便调试测试，以及后继的异步模式使用
12.门诊部分发送医嘱单元测试多线程测试建立在spring工具上
13.分析到门诊部分三个insert步骤在多线程下运行时间较长需要优化，建立多线程测试
##明日计划tomr plan：
  缓存接入
##其他未尽事宜Backlog
mybatis缓存接入 获取表格ddl生成分区模式ddl
分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能s40
s49
工作日志笔记记录日报
###当前工作curr：
门诊分区支持与测试
性能库存模块修改
ho移动护士后台端功能完善
增加眼别，院方提供眼别信息；核对基础信息 
分析原因解决问题 优化性能 门诊功能 与其他事项
成都医保接口
##今日工作today：
与马朋沟通 交流分析代码定位到新开医嘱发送时候的的库存变更，保存医嘱时库存不变更，只在发送时库存变更
分析智慧医保时间过长问题 与马棚沟通交流
缓存功能初步增加 为了方便调试增加了文件缓存与缓存刷新
分析医嘱发送时间 预计要分区了几个表
与肖鹏沟通交流日志不能打上的问题路径斜杠必须正斜杠 以及单元测试的自动化登录
分区表格ddl获取 通过数据库dump工具 Pgsql导出表格ddl的java调用命令行测试，不能输入密码，四处搜集资料，终于找到同步密码模式 测试ok
通过导出的sql文件分析ddl ，连接主表分区字段，获得主表ddl，测试通过
问题与马朋肖鹏沟通交流 医嘱发送单元测试，打上多个时间端点计算消耗时间与与马朋沟通医嘱发送单元测试的情况
分析医嘱发送时间的修改医嘱状态 添加医嘱抄送步骤 耗时较长，定位到xml文件里面updateVAF2_VBI2

##明日计划tomr plan：
 redis缓存接入
##其他未尽事宜Backlog
mybatis缓存接入 获取表格ddl生成分区模式ddl
分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能
s49

S48

工作日志笔记记录日报
###当前工作curr：
门诊分区支持与测试
性能库存模块修改
ho移动护士后台端功能完善
增加眼别，院方提供眼别信息；核对基础信息 
成都医保接口
分析原因解决问题 优化性能 门诊功能 与其他事项
##今日工作today：
1.与李雨淋马鹏张清华高鑫沟通分区信息与字段
分区了几个表
分区工具的获取表格主键功能
5.resteasy Java ws 完善部分单元测试
6.库存模块性能提升解决方案归纳总结
分区工具获取表格ddl方案总结 与资料搜集总结

##明日计划tomr plan：
分区表格ddl获取 redis缓存接入
##其他未尽事宜Backlog
mybatis缓存接入 获取表格ddl生成分区模式ddl
分区工具获取与分析索引ddl
根据主表索引ddl，生成子表索引ddl resume模式sql执行功能
s48
S44
工作日志笔记记录日报
##当前工作curr：
门诊分区支持与测试
增加眼别，院方提供眼别信息；核对基础信息 
成都医保接口
分析原因解决问题  优化性能 门诊功能  与其他事项  
##今日工作today：
与梁蓓蓓沟通 新开处方添加代理人信息功能开发
基础信息中考虑增加手术部位；核对基础信息
门诊信息表头显示设置测试完善 增加map模式 str模式
与张清华沟通讨论关于临时表清理资源收集gc方面的文档完善
Java ws前端增加部分单元测试
与高鑫马朋沟通交流分区方面的东西

 ##明日计划tomr plan：
门诊分区支持与测试 增加眼别，院方提供眼别信息
 ##其他未尽事宜Backlog
s44



S43

 * 张清华关于临时表清理资源收集gc
工作日志笔记记录日报
##当前工作curr：
门诊信息表头显示设置测试完善
、增加眼别，院方提供眼别信息；基础信息中考虑增加手术部位；核对基础信息
新开处方添加代理人信息功能开发
成都医保接口
分析原因解决问题  优化性能 门诊功能  与其他事项  
##今日工作today：
处方点评，查询处方记录 操作路劲护士系统 护理记录那块 处方点评那个问题 与梁蓓蓓肖鹏沟通交流测试
Solr索引遍历医院问题与高鑫肖鹏沟通交流
与马朋沟通交流ho移动端后台方面工作
门诊信息表头显示设置测试完善  增加dubbo接口 增加spring调用api
 Dubbo接口不能提供服务的排查与肖鹏沟通排除，花了不少时间
表头显示设的Dubbo单元测试增加，spring单元测试增加
  ##明日计划tomr plan：
新开处方添加代理人信息功能开发
增加眼别，院方提供眼别信息
 ##其他未尽事宜Backlog
s43


s43



工作日志笔记记录日报
##当前工作curr：
门诊信息表头显示设置 处方点评那个问题
、增加眼别，院方提供眼别信息；基础信息中考虑增加手术部位；核对基础信息
新开处方添加代理人信息功能开发
成都医保接口
分析原因解决问题  优化性能 门诊功能  与其他事项  
##今日工作today：
复诊根据参数判断是否测试血压与体重
复诊呼叫功能的文档总结整理
血透系统新开医嘱检查项目里面发送医嘱后，在门诊医生看不到条形码字串修正
索引sql增加with模式Mybatis单元测试工具版本完善，方便测试mybatis中配置的sql语法检验
Spring单元测试工具版本完善，去除dubbo配置，解决端口冲突的问题方便测试条形码问题 ，增加class模式
Url编解码工具增加对map的支持 查找分析几个编解码工具都不好用，提升可读性
血透系统看不到条形码问题分析与 新开医嘱方面的文档总结整理
门诊信息表头显示设置架构部分完善
提升可维护性问题总结

  ##明日计划tomr plan：
   门诊信息表头显示设置细节与测试  有处方点评那个问题
##其他未尽事宜Backlog
s42

工作日志笔记记录日报
##当前工作curr：
、增加眼别，院方提供眼别信息；基础信息中考虑增加手术部位；核对基础信息
4、新开处方添加代理人信息功能开发
5、成都医保接口
分析原因解决问题  优化性能 门诊功能  与其他事项  
##今日工作today：
修改测试环境配置启动跟踪到参数，反复启动测试了很多次 测试医嘱药品列表慢的问题，寻找到sql，
将参数手工带入到sql里面去，但是查询为空，解决这个为空的情况，估计可能mybatis发出的sql不同。准备抓取mybatsi发出的sql 或者手工替换的失误
初步对ide里面显示的map序列化字符串，做了反序列化，为了避免手工失误，做了自动化参数替换，带入sql 依然为空，估计是不能判断类型。需要把对象序列化为文件，不能直接使用默认的序列化字符串
建立最低mybats单元测试环境，吧配置文件迁移过来，准备连接本机抓取sql 。Mybatsi读取绝对路径的配置文件有问题，目前只能保持在class目录下 
 捕获真实环境的参数map，序列化保存为文件与反序列化测试。比较了几个序列化类库与方法 对象序列化以及ide里面显示的map序列化 。吧参数map文件附加上去，本地测试，果然有数据了，准备配置pg服务器日志记录
结果一番查找资料，配置log4j日志以及使用mybatis 获取sql api，进行Mybatis sql日志抓取，但是里面还有问号，不能抓到真实sql 。。
查找资料配置pg日志，初步不生效，与高鑫沟通交流pg日志配置问题，配置pgsql服务器日志，抓取真实sql 
Pgsql日志机制了解 ，配置日志依然抓取不到，使用navicate测试可以抓取到，说明配置上了，但mybatis发出的没有记录到
 同高鑫 肖鹏沟通系统一些情况
服务器sql日志记录不到，只好继续截获，结果排查，预计最终生成的sql可能在pgsql驱动上面，驱动源码比较复杂，先暂时自己实现生成测试
读取mybatis配置文件里面的sql ，查找资料么有找到自带的api，自己通过xml 读取实现了， 顺便比较了下几个xml类库做了总结，读取保存的map文件，自己实现sql参数带入，连续测试，增加了参数类型判断与sql参数格式转换，终于生成正确的sql 数据不为空了。
与 肖鹏、栾乐沟通交流 血透系统开检验申请单，没有生成条码问题分析
  ##明日计划tomr plan：
   继续当前工作的推进
##其他未尽事宜Backlog
s330


重启postgresql-x64-10

工作日志笔记记录日报
##当前工作curr：
分析原因解决问题  优化性能 门诊功能  与其他事项  
##今日工作today：
医嘱新开智能医嘱数据显示不出来问题分析，发现是solr问题

Sql优化情况分析
同高鑫 肖鹏沟通系统与Solr的情况
 与西安-开发 梁蓓蓓沟通关于门诊字段自定义设置 的问题
  ##明日计划tomr plan：
  继续性能优化与分析   门诊页面设置增加
##其他未尽事宜Backlog
S329





工作日志笔记记录日报
##当前工作curr：
分析原因解决问题 门诊功能 协助优化性能 与其他事项  
##今日工作today：
  数据库Sql优化分区机制测试与检索
 分区sql生成工具增加每周模式 方便建立分区索引等。
 分区每周模式测试 貌似效果依然不明显
准备测试下压缩数据模式怎么样，。搜集查询关于数据库压缩的资料
和高鑫沟通交流了一些导入导出出现的问题与总结解决 导入导出库 导入导出库到本地
字段压缩资料较少，直接启用os文件压缩测试。貌似影响不大。。
导入如到本地测试，发现速度有很大提升 同样的sql1.8s到0.4s。4s到1s。发现版本不同本地10.3，1.18 10.1 ，搜集pg10.3新特性看是否参数有改进
分析速度差异集中在db版本，配置设置，os，硬件可能都有影响
与西安-开发 梁蓓蓓沟通关于门诊页面设置增加的问题
  ##明日计划tomr plan：
门诊页面设置增加  继续性能优化与分析  
##其他未尽事宜Backlog
S328 


2018.3.27 工作日志笔记记录日报
##当前工作curr：
分析慢性能原因 协助优化性能 与其他事项 
##今日工作today：
与高鑫沟通交流索引方面的东西
 数据库Sql优化分区机制测试与检索
 与王杰沟通交流门诊医生项目方面的东西
门诊医生切换数据库测试
大表统计按照行数，体积 等
分区sql生成工具 方便建立分区索引等。
  ##明日计划tomr plan：
 继续性能优化与分析  
##其他未尽事宜Backlog



2018.3.26 工作日志笔记记录日报

##当前工作curr：
分析慢性能原因 协助优化性能 与其他事项 
##今日工作today：
与高鑫沟通交流索引检索机制以及查询数据库所有索引定义的存储位置，最终在系统库找到了索引的定义存储。。
数据库Sql优化Cte机制测试与检索
分区资料收集，初步测试，总结文档
与王杰沟通交流门诊医生项目方面的东西
  ##明日计划tomr plan：
 继续性能优化与分析  
##其他未尽事宜Backlog


图像方面的 api ，普通处理推荐使用命令行调用  GraphicsMagick  ImageMagick 。跨语言 跨系统 ，效果堪比ps   。。。各大语言自带的图形库和os图像库处理效果就比较一般了。      
高级处理可以使用opencv

 



















2018.3.6 工作日志笔记记录
当前工作：
今日工作：
入职办理
设备与软硬件环境搭建
当前项目沟通了解
与耿帅沟通 初步解决postgresql日志暴增的解决方案，待服务器验证
明日计划：
 熟悉项目，集成操作日志

2018.3.7  工作日志笔记记录
当前工作：
熟悉项目，集成操作日志
postgresql日志暴增的解决
今日工作：
项目本地环境搭建运行ok
初步dubbo 调用模式ok
postgresql日志暴增的解决第二版，与耿帅沟通测试
操作日志模块从freecms系统剥离，模块化，增加测试postgresql数据库版，增加rest接口 ，集成微服务提供远程接口，操作日志模块界面ui从struts mvc增加vue.js h5 mvc ，以及由此带来的界面通讯接口变更调试
协助同事胡朝境 关于小型java容器化 微服务springboot ，以及程序打包运行启动器方面的东东
明日计划：
 操作日志模块注解添加     mq消息管理部分沟通与使用

其他未尽事宜
操作日志模块查询部分完善，与分页完善 对移动端的兼容支持 增加dubbo分布式接口














2018.3.8  工作日志笔记记录
当前工作：
熟悉项目，集成操作日志 使用mq  注解集成
今日工作：
与韩磊宏沟通，关于mq方面的接口等。。Mq方面接入
日志操作日志模块注解添加 测试
搭建本地mq环境，发现mq的spring版本与微服务的冲突，使用单独的嵌入式tomcat来解决
完善通用版互操作接口，用来在api级别，cli命令行级别，rest web远程接口级别使用
完善嵌入式tomcat的使用以及注解mvc的实现。。。

协助同事行政关于注解使用 反射api以及堆栈api 等StackTraceElement
协助同事胡朝境嵌入式tomcat与微服务端口设置等
明日计划：
操作日志模块查询部分完善，与分页完善 对移动端的兼容支持 增加dubbo分布式接口

其他未尽事宜





2018.3.9  工作日志笔记记录日报
#当前工作：
 集成操作日志 使用mq  注解集成
#今日工作：
*增加dubbo分布式接口
*增加操作日志api文档说明
*增加翻页文档说明
*操作日志模块查询部分完善，
分页完善 集成easyui翻页插件与vue集成
移动端的兼容支持  移动端测试
#明日计划：
#其他未尽事宜Backlog
移动端测试 可能因为wifi网络问题，数据显示不全待修正








2018.3.12  工作日志笔记记录日报
#当前工作：
完善操作日志 熟悉业务 
#今日工作：
与杨经理沟通bug事宜 以及 日志事项
与高鑫(高鑫_西安开发)沟通交流 医生后台业务系统流程
与韩磊宏(韩磊宏 西安_开发) 沟通交流，提升日志模块稳定性
 #明日计划：
Bug处理与日志集成

#其他未尽事宜Backlog



















.
2018.3.13  工作日志笔记记录日报

#当前工作：
完善操作日志 熟悉业务  
#今日工作：
业务继续熟悉，初步查看bug问题
吧日志功能集成入 cloudcommons 了。Spring注解版与普通注解版
Spring注解日志功能实现文档与 使用api文档手册撰写
 #明日计划：
集成测试 日志功能看有无类库冲突。。以及在调用项目集成测试
#其他未尽事宜Backlog

 









2018.3.14  工作日志笔记记录日报
#当前工作：
完善操作日志 熟悉业务  
#今日工作：
与杨经理沟通类库jar精简问题
 和韩磊红 沟通mq类库的问题，再次联调。。租后决定吧mq那边实现，以便精简mq包
和肖鹏沟通postgresql类库问题  ，确认删除了db包
Aspect包问题，确认添加
再次沟通，决定依然日志模块微服务模式rest接口
调整本机业务系统环境

 #明日计划：
日志模块 common库分支版本合并回 独立日志模块主干
本机业务中集成测试日志模块
 #其他未尽事宜Backlog






那我尽可能提交的时候把依赖都加上。。。。大家遇到编译错误可以忽略呀  忽略掉编译错误的java 正常java文件可以正常编译为class文件的。提升开发效率


2018.3.15  工作日志笔记记录日报
#当前工作：
完善操作日志 熟悉业务  
#今日工作：
初步分析代码，关联界面按钮与后端代码的关联 分析深入阅读代码
接入日志，代码量多，准备接入日志工具jar。。解决日志工具jar jdk版本编译不同匹配问题。。
简化工具类，增加 rest接口的api sdk转接口，方便使用
接入医院后台测试新开医嘱，发现日志模块包400 http错误。经过多重测试，估计可能是参数太长导致的，吧日志模块http模块增加post方法，在此测试ok
合并到common库，精简调用api到 一行，切换数据库测试，增加配置文件测试
日志模块 common库分支版本合并回 独立日志模块主干
本机业务中集成测试日志模块
保存为json mybatis调整花了点时间。Prop文件跨项目读取花了点时间修正完善

 #明日计划：
集成测试
 #其他未尽事宜Backlog


2018.3.16  工作日志笔记记录日报
#当前工作：
完善操作日志 优化代码 分析bug 与其他事项  
#今日工作：
 读取配置文件增加once模式。。
调整相关工具类命名，防止mybatis运行冲突。
协助同事王杰调优sql 性能问题。定位到具体若干行数，发现了个缺失索引，增加，测试发小改善不明显，在此扫描，发现是连接了一个视图造成的，打开视图比较复杂，反复测试定位了此问题。使用物化视图优化，增加测试视图测试效果很好解决了此问题。对物化视图的更新问题测试，触发器机制与定时机制或编程语言触发机制等解决方案。。
综合各大sql优化方法，尽可能完善了性能优化方面的文档
查找json字段的update，测试了好多方法，貌似只能整体更新，不能对某个内部json field更新。。总结了postgre json字段的操作文档总结。
与同事行政沟通json字段update问题，经过一番他的查找资料，得到相同结论只能整体更新
协助同事王杰tomcat与java app在eclipse环境下的heap 内存溢出解决，以及permgen  space调整。很久没用tomcat插件了，细节方面与张清华 西安_开发沟通交流这个tomcat情况。完善了下eclipse tomcat插件的发布与运行 调整机制。
与韩磊宏沟通，mybatis对json字段的调整，对json字段做了重复性约束索引uniq，测试总结 。交流mq消息系统queue模式的一些情况。
 #明日计划：
 #其他未尽事宜Backlog






























2018.3.19  工作日志笔记记录日报
#当前工作：
分析慢查询sql的原因  优化sql 与其他事项  
#今日工作：
开会沟通分析慢查询sql 的情况
和同事王杰  高鑫沟通宝田库的情况
协助高鑫join问题的解决 
和耿帅沟通肇庆库情况
搜集资料文档Pgsql 数据库关于索引 表行数 表数据 索引数据统计的sql统计，以便进行比较 方便找出慢查询原因
搜集资料优化方法大总结
从远程库获取数据库统计信息  索引信息以及数据表记录数量等。方便对比
  #明日计划：
对比索引，对比 数据总量对比 数据行数对比语分布 尽可能找出问题所在
 #其他未尽事宜Backlog







2018.3.20 工作日志笔记记录日报
##当前工作curr：
分析慢查询sql的原因 优化sql 与其他事项 
##今日工作today：
仔细对比从远程库获取数据库统计信息 索引信息以及数据表记录数量等
查询资料关于数据集合连接join算法的几种具体实现
对比同样sql在不同库的执行计划
查找分析资料关于数据库优化rbo cbo方面的。
分析sql语句，使用了函数貌似不少，可以使用函数索引优化，查找pgsql函数索引方面的资料搜集分析
尝试吧视图转化为函数索引，函数返回记录集方式，貌似不能生效
 与同事王杰 高鑫沟通分析情况
整理资料优化方法大总结 
搜集整理pgsql新特性，看能否为我所用
 ##明日计划tomr plan：
物化视图的自动更新 触发器函数实现 函数索引的实现
##其他未尽事宜Backlog





2018.3.21 工作日志笔记记录日报
##当前工作curr：
分析慢性能原因 协助优化性能 与其他事项 
##今日工作today：
物化视图+触发器模式下的并发测试
物化视图的自动更新 触发器函数实现 函数索引的实现
增加物化视图java代码按时更新模式与测试
协助同事张清华关于pgsql汉字排序的问题
协助同事王杰性能问题分析
 在18库上使用实际库测试效果，不同的并发数量下的测试，以及禁用打开触发器模式的测试
为行政高鑫提供csdn账号帮助 以便下载项目所需重要资源
  ##明日计划tomr plan：
继续性能优化与分析
##其他未尽事宜Backlog






2018.3.22 工作日志笔记记录日报
##当前工作curr：
分析慢性能原因 协助优化性能 与其他事项 
##今日工作today：
查看门诊医生项目代码，流程测试。一些问题语同事交流解决
仔细查看了一些项目功能方面的代码 ，做了对应的文档总结，方便检索
发现门诊医生首页ajax数据加载过大7M之多，需要优化，评估优化体积只有600kb，会有很大提升
搜集压缩方面的资料语整理。。Tomcat也支持设置gzip压缩
搜集资料设置tomcat的gzip压缩设置，但是在eclipse 环境下tomcat插件配置比较麻烦，经过一番分析，分析了tomcat插件配置文件所在，不知为什么设置了gzip不生效，只好使用filter模式实现了。
搜集资料做filter，成功实现了gzip压缩。经过测试7M的ajax数据压缩到800kb效果明显。首页其他文件也从3M压缩到600KB
eclipse tomcat插件配置文档整理更新
排查了其他几个页面的，也发现了若干个大数据加载需要优化的地方，整体几乎每个页面都有2-3M，很有必要优化
与高鑫沟通吧压缩配置到18测试服务器上以及测试效果

  ##明日计划tomr plan：
 继续性能优化与分析  完善压缩插件（排除图片等 url分析排除语设置 其他参数完善）
门诊医生代码继续熟悉 分析appcache机制 语其他cache机制优化性能
##其他未尽事宜Backlog





2018.3.23 工作日志笔记记录日报

##当前工作curr：
分析慢性能原因 协助优化性能 与其他事项 
##今日工作today：
压缩过滤器增加了对文件扩展名的排除 jpg png gif 以及 mime类型名单 json css js html类型的压缩。增加了对小体积文件的排除
对多个浏览器的支持压缩模式做了下测试统计，基本都支持gzip deflate模式，测试了下deflat模式，貌似和gzip效率差不多。
对特定业务数据压缩方法评估测试  json数字索引 csv格式  时间戳格式 json数字索引效果减少了约40%数据量，Csv格式在此基础上又可减少30% 时节戳模式减少10%
  对比不同汉字编码对数据体积的影响，比较大，gbk比utf可以体积缩小50%左右，压缩后依然这么影响存在。查找编码方面资料与整理 
大概规划了下企业内部汉字编码标准uke编码 ，以及对垂直领域医疗行业文字分析，预估垂直领域内一千字即可覆盖。通过对实际数据测试，因为实际数据汉字相对较少，更改未gbk编码后体积减少5--10%，不是很明显，先暂时不动文字编码这块
测试Appchache 以及CacheStorage 机制是的使用，appcache不好用，CacheStorage 改动较大，先不用
测试indexdb本地存储cache，做了api二次包装，使它简单化。实际效果不错，但是异步api使用比较麻烦 。。
对门诊首页增加了localStorage  本地cache模式，这个简单易用，效果显著，
协助同事行政关于压缩gzip的设置与使用，转发tomcat插件设置文档
  ##明日计划tomr plan：
 继续性能优化与分析  完善压缩插件（url分析排除语设置 超大数据读取体积的优化）
门诊医生代码继续熟悉 分析appcache机制 语其他cache机制优化性能
##其他未尽事宜Backlog






