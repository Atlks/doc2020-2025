Atitit 提升性能 spring laze load和datasource 懒加载


（2）如何验证一个bean是否进行了lazy加载，
通过调试，在如下断点处，可以查看Context->beanFactory->SingletonObjects中是否包含了名字为“sonService”的对象，如果没有，则说明是lazy加载



1）第一步 在spring 的所有xml中配置lazy属性，不能只在根xml中配置。




Spring IOC实现DataSource的lazy加载
目录 [隐藏]
1 问题描述
2 分析&解决
3 总结
4 测试
5 后续维护
附:其他尝试
附：参考文献
本文概览：介绍如何实现dataDataSource的lazy加载。好处在于：（1）对于不同任务，其实依赖dataSoruce不同，不会因为不相干的数据库挂掉，而阻塞任务；（2）而且还有另外一个好处在于减少不必要连接数，只初始化用到的dataSourche。
1 问题描述
1、问题引入
在一个非服务类型的java项目中,有一个数据库对应海森堡服务总是挂掉，导致所有所有任务都没办法执行，其实这样是不合理的，因为对于没有用到这个数据库的任务应该是能够正常执行的。
可以把这个问题泛化下，就是在一个项目中，每一个任务其实依赖的数据库不同，如下图，假设数据库C挂了，那么此时任务1不应该被阻塞，只是任务2会被阻塞。为了解决这个问题，引入了DataSource的Lazy加载。

2、环境
Spirng：3.2.3.RELEASE
Mybatis：3.4.1
Mybatis-Spring:1.3.0
Druid：1.0.2.7
2 分析&解决
可以采用Spring Lazy的加载方式：只有需要的时候，才会初始化到Spring 容器中。这样对于每一个任务只加载他们需要的DataSource就可以了。
具体步骤如下：
1、【Step1】 如果有多个spring 配置文件，需要在每一个spring的xml文件中配置全局
“如果一个bean被设置为延迟初始化，而另一个非延迟初始化的singleton bean依赖于它，那么当ApplicationContext提前实例化这个非延迟的singleton bean时，它必须也确保所有上述singleton 依赖的bean被预先初始化，当然也包括设置为延迟实例化的bean。”
当设置DataSource以lazy方式加载时，那么依赖这个DataSource的所有上层类都要设置为lazy方式。如果通过@Lazy对每一个类进行设置的话，这样改动修改类比较多，而且其他同学在新定义一个类时，很容易丢失这个配置，所以这里设置为全局lazy。设置成lazy的全局加载时，必须在每一个xml文件中进行如下设置，不能仅仅在root的xml中设置：

2、【step 2】 出现错误
错误日志信息为:
Pre-instantiating singletons in org.springframework.beans.factory.support.DefaultListableBeanFactory@657189ad: defining beans [org.springframework.context.support.PropertySourcesPlaceholderConfigurer#0,org.springframework.aop.config.internalAutoProxyCreator,org.springframework.transaction.annotation.AnnotationTransactionAttributeSource#0,org.springframework.transaction.interceptor.TransactionInterceptor#0,org.springframework.transaction.config.internalTransactionAdvisor,dataSource,sqlSessionFactory,mapperScannerConfigurer,sqlSession,transactionManager,dataSource2,sqlSessionFactory2,mapperScannerConfigurer2,sqlSession2,transactionManager2,jdbcTemplate,timeOutService,transactionService,org.springframework.context.annotation.internalConfigurationAnnotationProcessor,org.springframework.context.annotation.internalAutowiredAnnotationProcessor,org.springframework.context.annotation.internalRequiredAnnotationProcessor,org.springframework.context.annotation.internalCommonAnnotationProcessor,studentDaoWithJdbcTemplate,studentDaoWithJdbc,studentDaoWithSqlSession,multiDataSourceAspect,advice1,advice2,org.springframework.aop.support.DefaultBeanFactoryPointcutAdvisor#0,org.springframework.aop.support.DefaultBeanFactoryPointcutAdvisor#1,org.springframework.context.annotation.ConfigurationClassPostProcessor.importAwareProcessor,studentDao,newStudentDao]; root of factory hierarchy
21:18:22.175 [main] ERROR com.alibaba.druid.pool.DruidDataSource – init datasource error, url: jdbc:mysql://127.0.0.1:3306/test
com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException: Unknown database ‘test’
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:526)
    at com.mysql.jdbc.Util.handleNewInstance(Util.java:389)
（1）最初以为是<context:component-scan… />覆盖了全局lazy属性 的问题
但是Spring 在2.1-m4 版本中已经修复这个问题了。https://jira.spring.io/browse/SPR-3823
（2）分析错误信息
查看IOC初始化的源码，进行如下断点，发现mybatis扫描的mapper类的lazyInit属性都是false，全局设置的lazy属性没有生效。

所以，为了将这个bean变为lazy=true，这里通过对需要lazy加载的mapper接口中添加@Lazy注解：

3、【step 3】发现还是报错
（1）错误日志信息如下：
at org.springframework.context.support.AbstractApplicationContext.finishRefresh(AbstractApplicationContext.java:948)
    at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:482)
    at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:139)
    at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:83)
发现【Step2】中bean可以进行lazy加载了，但是DataSource会执行init，此时在DataSource配置中，把init方法去掉，如下 。(查看了DruidDataSource，在使用时，如果没有执行init()，它还会执行init的，所以这里去掉也没有关系)。
<bean id=”dataSource” class=”com.alibaba.druid.pool.DruidDataSource” init-method=”init” destroy-method=”close”>
修改为   
<bean id=”dataSource” class=”com.alibaba.druid.pool.DruidDataSource”  destroy-method=”close”>
（2）如何验证一个bean是否进行了lazy加载，
通过调试，在如下断点处，可以查看Context->beanFactory->SingletonObjects中是否包含了名字为“sonService”的对象，如果没有，则说明是lazy加载。

3 总结
1、一般会将某些任务特殊依赖的DataSource设置成lazy加载，对于公用的DataSource不需要设置成lazy加载。这样好处在于：
（1）对于不同任务，其实依赖dataSoruce不同，不会因为不相干的数据库挂掉，而阻塞任务。
（2）而且可以减少不必要连接数，只会初始化任务用到的dataSource，没有用到dataSource不会被初始化 。
在设置lazy加载DataSource的任务之后，可以在日志中查看是否还包含任务不依赖的DataSource的初始化日志信息。
2、设置lazy加载DataSource的步骤如下：
（1）第一步 在spring 的所有xml中配置lazy属性，不能只在根xml中配置。

（2）第二步  对于需要进行lazy加载的DataSource作如下处理
对应的mapper接口加上注解@Lazy

在DataSource配置中，把init方法去掉。如下
<bean id=”dataSource” class=”com.alibaba.druid.pool.DruidDataSource” init-method=”init” destroy-method=”close”>
修改为   
<bean id=”dataSource” class=”com.alibaba.druid.pool.DruidDataSource”  destroy-method=”close”>
3、注意
本次处理都是针对非服务类型的项目，但是对于服务类型的项目，还是建议采用非lazy方式加载dataSource。
4 测试
定义一个DataSource1、DataSource2和ServiceA。假设ServiceA依赖DataSource1，DateSource2对应的数据库是好的，DataSource2对应的数据库是坏的。分两种情况进行测试，
情况1：不对DataSource2进行懒加载，此时程序启动时报错。
情况2：对DataSource2进行懒加载，此时程序可以正常运行。
注意：可以通过配置数据2地址为一个错误地址，来模拟数据库实例挂掉，不一定要kill掉。
5 后续维护
1、如果将来有需求需要增加spring xml 文件，需要设置全局lazy属性

2、如果需要新增数据库mapper，若mapper不是公用的，即如果只是新增任务使用的话， 需要lazy加载DataSource:
（1）对应的mapper接口加上注解@Lazy

（2）在DataSource配置中，把init方法去掉。如下
<bean id=”dataSource” class=”com.alibaba.druid.pool.DruidDataSource” init-method=”init” destroy-method=”close”>
修改为   
<bean id=”dataSource” class=”com.alibaba.druid.pool.DruidDataSource”  destroy-method=”close”>

