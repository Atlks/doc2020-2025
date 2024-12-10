Atitit enhance dev  eff  read req提升开发效率 可读性规范


提升效率的俩大原则
Kiss原则简单原则
可读性原则

命名规范 见名字知道意思
大力使用中文提升可读性
层次结构缩减 单层 vs 双层
Static 函数 vs oop
代码结构扁平化 项目 模块模式
不要树形嵌套过深。。一般项目双层足够

缩减项目文件数量与代码数量
使用简洁模式 减少不必要的文件 
使用dsl 4gl、 sql 模式大力缩减代码
代码业务抽象通用化  库表查询 操作

不要使用重量级模式
 Dp的实现 servicelocator模式也很好，由于Ioc实现模式
使用易于理解的模式
Vue里面使用js模式，不要npm模式
Other
尽可能使用默认模式
使用gradle代替maven

存在的问题
不要使用webpacket打包模式麻烦
Springboot、 ioc的实先
可以使用springboot的web rest接口。。但不要ioc。。使用简单的new serviceloctor模式就解决了dp问题

太多泛滥的接口
层次过多哦
Gradle自定义过多复杂
