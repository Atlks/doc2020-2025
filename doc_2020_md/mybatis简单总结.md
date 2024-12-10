mybatis
	1.介绍mybatis的框架的原理,优点,缺点
		是一个优秀的半orm持久层框架,对jdbc进行的封装;
		优点:可以灵活的操作sql语句(可以对sql语句进行自定义的优化)
		缺点:不是全自动的orm框架,不能自动生成表,sql语句
		
	2.使用mybatis:
		A:导入jar包
		B:创建mybatis全局配置文件(sqlMapConfig.xml/mybatis-config.xml)
		C:使用mapper代理实现对数据的操作(使用约定)
			A:接口中的方法名称和mapper.xml中的id一致
			B:入参类型要和方法中的参数类型一致(一般使用包装类型)
			C:出参类型要和返回值的类型一致(如果是list集合,返回的是泛型的类型)
			D:命名空间是接口的全路径(如果有mapper.xml文件就必须提供命名空间)
			
	3.参数绑定:
		A:基本类型:
			a:一个参数的,直接使用#{任意}
			b:多个参数的,使用@Param注解
		B:pojo
			直接使用,使用#{属性名称}
		C:数组
			使用@Param注解或者使用array
		D:list集合
			使用@Param注解或者使用list 或者 collection
		E:map集合
			使用@Param注解,map
			
	4.自定义映射
		主要使用在数据库的字段和pojo中不一致时;
		
		一对一关系:
			在一的一方,声明另一个表的pojo
			assocation  javaType 
		
		一对多关系:
			在一的一方声明一个多的一方的集合,在多的一方声明一的一方的pojo
			collection	ofType
		
		多对多关系:
			在两个pojo类中相互声明对方法list集合
			collection	ofType
			
	5.懒加载
		作用是优化查询,按需加载,在需要查询某些条件是在sql语句加载进去,完成查询;
					
	6.动态sql
		判断:
		循环:
		where标签:
		sql片段:
		trim标签:
		set标签:
		
	7.缓存
		一级缓存:默认一直开启,无法关闭的
		二级缓存:默认是开启的,但是需要在napper.xml中配置开启
		第三方缓存:在使用二级缓存的基础上,在mapper.xml中配置使用
		
