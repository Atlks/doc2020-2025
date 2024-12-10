Atitit 提升稳定性  fix t66

Crash-only 模式

Crash-only software refers to computer programs that handle failures by simply restarting, without attempting any sophisticated recover



客户端负载均衡 vs 服务端

客户端》 服务端

Cookie vs session


适当分布式模式

单体应用的另一问题就是可靠性。由于所有模块都运行在同一进程中，任何模块中的一个 bug，比如内存泄漏都可能弄垮整个进程；此外，由于应用中的所有实例都是唯一，这个 bug 将影响整个应用的可用性。
