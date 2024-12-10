Atitit 稳定性提升的艺术 之技术解决之道



2. 为什么会发生稳定性问题	1
2.1. 单点故障(单点故障率较高)	1
2.2. 复杂	1
2.3. 资源耗尽	1
2.4. 死锁与等待	1
2.5. 崩溃	1

大原则
尽快释放资源类似php最好的稳定性
Nginx 负载均衡 排除单点故障
分离 隔离故障

Crash-only 模式  自动重启服务 守护
Crash-only software refers to computer programs that handle failures by simply restarting, without attempting any sophisticated recover

语言与架构级别提升
彻底的前后端分离
多进程  前端使用php ngihx做加载
. Atitit 提升稳定性 错误处理 全局错误捕获

技术管理上的举措
压力测试
预生产环节
4. 稳定性测试	3
4.1. Throw ex测试	3
4.2. 断开连接测试	3
4.3. 多线程测试并发	3

单元测试


atitti 提升稳定性的艺术之程序代码级别稳定性的艺术  attialx著 atl著  
