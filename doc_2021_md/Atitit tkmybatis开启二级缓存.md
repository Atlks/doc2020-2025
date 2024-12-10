Atitit tkmybatis开启二级缓存 


、 //公司表cache填充
		List<Company> list = companyService.getAllEnable();//db rd
		
		System.out.println(companyService.getAllEnable());
		

如果没有生效，可能是引用对jar没有更新，，重新打包common项目，然后update要使用对项目。。。


再次查询可以看到sql少了一条。。Mybatis cache提示命中类条缓存。。


19:56:47,947 DEBUG org.apache.ibatis.cache.decorators.LoggingCache - Cache Hit Ratio [application.dao.CompanyMapper]: 0.5_frmlog4j
[application.model.Company@4f2d014a, application.model.Company@51fc862e]
