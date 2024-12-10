Atitit 常见项目大问题以及解决方案


定位错误信息不能显示被隐藏
开启框架的debug trace模式
去除cache
去除全局err handler （php有三个全局handler
去除无谓的重定向。。（nginx apache 以及代码重定向
去除所谓的友好页。。（起码在测试环境下
无法生成日志文件情况下，可以试试session零时内存存储
增加日志或session记录日志。。
管理平台看是否有配置显示debug模式


数据不同步更新不及时 不生效
去除cache
管理平台看是否有配置去除cache

