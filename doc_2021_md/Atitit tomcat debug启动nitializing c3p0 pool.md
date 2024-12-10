Atitit tomcat debug启动nitializing c3p0 pool... com.mchange.v2.c3p0.ComboPooledDataSource 启动卡住

如果非debug模式是可以启动的，embed tomcat8.5 

图， 程序启动的时候直接卡在了 Initializing c3p0 pool... com.mchange.v2.c3p0.ComboPooledDataSource 这一句，后面就没日志了。

，导致像卡住了。把日志开到debug级别，再启动：

会发现，其实日志是有的， mybaits一直在加载mapper。
这里其实是mybatis结合spring时的一个坑，当mapper文件有语法错误时，spring会循环重试。但是。。没有打印log出来。解决方案是重写sqlsessionfactory，把日志打出来：
/**
 * @author: zenghong
 * @Date: 2019/9/3 09:42
 * @Description: 重写sqlsessionfactory，解决ibatis+spring，当mapper语法错误时，无异常日志，无限重复加载的问题。
 */public class MySqlSessionFactory extends SqlSessionFactoryBean {
    @Override
    protected SqlSessionFactory buildSqlSessionFactory() throws IOException {
        try {
            return super.buildSqlSessionFactory();
        }catch (Exception e){
            e.printStackTrace();
            throw e;
        }finally {
            ErrorContext.instance().reset();
        }

    }}


然后 factory改成重写这个：
 <bean id="writeSqlSessionFactory" class="com.jccfc.worker.center.dal.MySqlSessionFactory">
    <!--<bean id="writeSqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">-->
        <property name="dataSource" ref="writeDataSource"/>
        <property name="configLocation" value="classpath:mybatis/mybatis-config.xml"/>
        <property name="mapperLocations" value="classpath:mybatis/mapper/*.xml"/>
    </bean>


 此时有报错

java.lang.NoClassDefFoundError: org.springframework.beans.FatalBeanException

手动加载到build目录里面去不行，，放入tomcat web-info/lib也找不到。。

只好让如jdk、ext ，这时候就找到了。。可以debug启动了。。。




