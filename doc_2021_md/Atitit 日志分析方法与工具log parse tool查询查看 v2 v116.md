Atitit 日志分析方法与工具log parse tool查询查看 v2 v116


日志与流程对对应关系   for case一一对应即可，，观看日志即可重现重要流程

所有对io都要记录，net rest，sql，rds等。。

摘要摘取  正则表达式

Grep tag关键词

Logger classname作为常见组件tag

一般  grep  tag 即可。。

跨组件使用线程main查询作为tag
查询所有可以使用 main作为tag

某个方法可以单独一个log
查询某个订单可以查询出其使用对线程号，然后使用线程号作为搜索条件，得到某个订单的处理权流程
日志可视化工具
日志可视化工具LogVisualizer
一般都是采用ELK技术栈进行处理
