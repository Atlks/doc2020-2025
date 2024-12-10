Atitit mybatis 二级缓存开启测试  


通过打开debug sql日志看到是否启用

正常情况下，只有第一个发出sql。。。


如果没有看到 ，可能是sesseon没有sumibt ,,submit ha zo ok//


	private static void testMybatisCache(String cfg) {
		HashMap map = new HashMap();
		Object productId=9999;
		map.put("productId", productId);
		Object programId=9999;
		map.put("programId", programId);
		Object paramNo=12;
		map.put("paramNo", paramNo);
		SqlSession ss = MybatisUtil.getSqlSessionNew(cfg);
		lgr.info("$$$$$$$$$$$$ SqlSession id " + ss.toString());
		MybatisUtil MybatisUtil1 = new MybatisUtil();
	  Object rzt= ss.selectOne("CliSendAdvice.getParameter", map);
	  ss.close();
	    System.out.println(rzt);
	}


、二级缓存 
二级缓存(second level cache)，全局作用域缓存；二级缓存默认不开启，需要手动配置
MyBatis提供二级缓存的接口以及实现，缓存实现要求 POJO实现Serializable接口
二级缓存在 SqlSession 关闭或提交之后才会生效

