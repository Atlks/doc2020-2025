 Atitit 基于dsl的Rest 接口通讯解决方案

1.1. 1.1. Overview概论		1
1.2. 1.2. Function & Feature功能特性		1
1.2.1. 直接传递dsl到后端反射解析即可	1
1.2.2. Dsl语法与java c# php js等流行语言一致，可以直接在ide里面测试	1
1.2.3. 多序列化支持xml,json,toml	1
1.2.4. 随机数参数支持防止ajax缓存rdm=0.111222157474897	2
1.2.5. Ioc容器参数支持，可以在页面级别指定ioc配置	2
1.2.6. 异常处理支持，也可指定返回码模式	2


1.1. Overview概论	
主要为了解决目前的rest接口配置繁琐的问题。以及扩展性的问题。提升灵活性
1.2. Function & Feature功能特性	

直接传递dsl到后端反射解析即可
http://www.a.com/rest?dsl=new com.atti.com.mod1.class1().meth1(123).meth2(‘test’)

Dsl语法与java c# php js等流行语言一致，可以直接在ide里面测试
多序列化支持xml,json,toml
目前主要实现json。。其他的已经规划。
Datatype参数

随机数参数支持防止ajax缓存rdm=0.111222157474897
Ioc容器参数支持，可以在页面级别指定ioc配置
异常处理支持，也可指定返回码模式
Api异常处理机制非常好，将其移植到rest接口上面


