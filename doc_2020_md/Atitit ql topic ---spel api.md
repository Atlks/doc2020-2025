Atitit ql topic ---spel api

功能分类4大类


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

查询语句

查询单个属性节点 字段
	String expressionString = "#root['data'][0]['id']";

From #root['data'] where id《10003 
	
	  expressionString = "#root['data'].?[['id']<10003]";
	//"#myMap.?[key.length()<5&&value>90]"

(···条消息)Spring表达式语言：SpEL语法_Java_VipMao的博客-CSDN博客
