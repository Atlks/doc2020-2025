Atitit 时间戳补充

时间戳 10位是秒级
13位是毫秒

时间戳转换不正确在java得不到 data...must long type ..then ok...if int error..

	long time=(long)1586591592*(long)1000;
	   //   1586591592045  //ms
	System.out.println( new Date().getTime());  //gettime  ms timestamp   13bit ms  
	//毫秒级时间戳
long currentTimeMillis = System.currentTimeMillis();
System.out.println(currentTimeMillis );
	
	 String result2 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format( time );
	    System.out.println(" " + result2);

