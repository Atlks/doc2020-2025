Atitit 项目性能提升总结kok案例


及时性问题
直接接口转发，减少查库时间
 
落库
大力减少更改，不要使用replace，，insert on dulip uopdate
触发器检查约束
Insert ingore delaye 模式
多线程模式

减少死锁

单条事务

Join过多  
款表模式，，使用触发器同步


