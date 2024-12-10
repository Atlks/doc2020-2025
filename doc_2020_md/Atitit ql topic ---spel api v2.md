Atitit ql topic ---spel api

功能分类4大类
5：调用方法	13
6：算术、比较、赋值、三元运算符	16
12：表达式模板	36


功能具体
Spring表达式语言：SpEL语法	2
1：直接量表达式	3
2：在表达式中创建数组	5
3：在表达式中创建List集合	7
4：SpEL中访问List、Map等元素集合	9
5：调用方法	13
6：算术、比较、赋值、三元运算符	16
7：类型运算符	19
8:调用构造器	21
9：安全导航操作	23
10:集合的选择	26
11：集合的投影	29
12：表达式模板	36

12：表达式模板	36

String sql = "insert  into football_match_t(  id,match_event_id, match_status ,match_time,tee_time,"
//						+ "home_id,away_id,which_round,neutral_site,create_time,delete_flag,match_detail,"
//						+ "animation,intelligence,squad,video)values("
//						+ "#{[id]},'#{[match_event_id]}','#{[match_status]}','#{[match_time]}','#{[tee_time]}',"
//						+ "#{[home_id]},#{[away_id]},#{[which_round]},#{[neutral_site]},now(),0, '#{[match_time]}',"
//						+ "0,0,0,0)";
//				// sql = processVars(sql, json.getAsJsonObject("data") );
//				sql = QlSpelUtil.parse(sql, param);
//				logger.info(sql);
//
5：调用方法	13
T(class).m1(“xxxx”,”bbbb”)
New pkg.class().m1()

4：SpEL中访问List、Map等元素集合	9


查询语句

安全导航查询单个属性节点 字段
	String expressionString = "#root['data'][0]['id']";

9：安全导航操作	23
10:集合的选择	26
11：集合的投影	29


From #root['data'] where id《10003 
	
	  expressionString = "#root['data'].?[['id']<10003]";
	//"#myMap.?[key.length()<5&&value>90]"

(···条消息)Spring表达式语言：SpEL语法_Java_VipMao的博客-CSDN博客
