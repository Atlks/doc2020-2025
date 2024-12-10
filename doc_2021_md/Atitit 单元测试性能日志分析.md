Atitit 单元测试性能日志分析日志分析法

添加适当对日志性能埋点

增加rest接口和sql的时间分析，
对循环，要列出循环数量


Spring框架加载4s

初始化了俩个线程池花了 14 s ，这个可以去除
2020-12月-16 20:03:36,378-[TS] INFO main com.alibaba.druid.pool.DruidDataSource - {dataSource-1} inited
 2020-12月-16 20:03:44,886-[TS] INFO main com.alibaba.druid.pool.DruidDataSource - {dataSource-2} inited
2020-12月-16 20:03:50,903-[TS] INFO main application.web.quartz.HKLhcSchedule - HK六合彩-开始同步开奖数据







2020-12月-16 20:03:55,571-[TS] INFO main application.util.HttpUtils - HttpUtils.post-url:http://52.229.156.88/lottery/getDataInfo?token=e1254c5289ae26f83d020ccfc517c769
2020-12月-16 20:04:16,572-[TS] INFO main application.util.HttpUtils - HttpUtils.post-exception-url:http://52.229.156.88/lottery/getDataInfo?token=e1254c5289ae26f83d020ccfc517c769
