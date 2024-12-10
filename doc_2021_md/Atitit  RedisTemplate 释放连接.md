Atitit  RedisTemplate 释放连接

默认释放不掉。。使用closeconn都不行。。。貌似是static对。。
使用thrd包装也释放不掉。。

使用classload也不行。。 最后使用它依赖对lettuce  api来实现即可。。。



	for (int i=0;i<1000;i++) {

			 try {
				 
				 ResourceBundle resource = ResourceBundle.getBundle("redis");
					String host = resource.getString("spring.redis.host");

					 
					String pwd = resource.getString("spring.redis.password");
				 RedisURI RedisURI1 = RedisURI.create("redis://"+host+":6379");
				 RedisURI1.setPassword(pwd);
				RedisClient client = RedisClient.create(RedisURI1);
			//	client.se
			        StatefulRedisConnection<String,String> connect = client.connect();
			      //  connect.se

			        /**
			         * 同步调用
			         */
			        RedisCommands<String,String> commands = connect.sync();
			        commands.select(10);
			        commands.set("hello"+i,"hello world"+i);
//			        String str = commands.get("hello");
//			        System.out.println(str);
			        connect.close();
			        client.shutdown();
				//	foreachClsldr(i);
					
			} catch (Exception e) {
				e.printStackTrace();
			}
 	
		 :0>info clients
