Atitit uri url格式规范与解析  带端口用户名、密码


一、URL，统一资源定位器。指向互联网上的“资源”，可协议名、主机、端口和资源组成
如: http://username:password@host:8080/directory/file?query#ref:
Component	Example value	Also known as
Protocol	http	scheme
Authority	username:password@host:8080	 
User Info	username:password	 
Host	host	 
Port	8080	 
File	/directory/file?query	 
Path	/directory/file	 
Query	query	 
Ref	ref	fragment
--------------------- 
URL url = new URL (string);
		String[] a=string.split(":");
		this.setScpAddress(url.getHost()).setScpPort("22").setUsername("root")
		.setPassword(url.getUserInfo().split(":")[1]);
访问带有用户名、密码保护的 URL


	string = "    -url   http://user1:ttredis$2018*124@101.132.148.11:63790/1 -get access_token";


