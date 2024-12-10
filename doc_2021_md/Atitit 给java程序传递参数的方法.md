Atitit 给java程序传递参数的方法


-D jvm参数，可读性高 推荐


		log.info("System.getProperties:"+JSON.toJSONString(System.getProperties(),true) );
		int trx_timeout = Integer.parseInt( System.getProperty("sqlTimeout", "15"));// double 7s


 // java   -DsqlTimeout=15   -Dsleeptime=7 -cp  C:\Users\jun\eclipse-workspace\deadlockchk\target\classes;C:\Users\jun\eclipse-workspace\deadlockchk\lib\*  deadlockPrj.deadlockCheck 
//   -Dcfgfile=cfgloc 

Main方法参数，可读性低。。




