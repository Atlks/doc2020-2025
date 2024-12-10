Atitit 表达式语言 调用 java  


Atitit java 动态表达式调用类方法   最佳实践  Ognl  新来的MVE Beanshell  Groovy


目录
1.1. Beanshell 可以的	1
1.2. MVEL 好像没有找到	1
1.3. Ongl可以的。。	1
1.4. Groovy	2


 老牌的Ognl(老到网站都找不到了) 新来的MVEL 国产的Aviator 目前最快的JSEL:JSEL测试表达式
3.4. Spel （调用java等扩展，集合投影选择等）	2


3.5. Ongl （调用java等扩展，集合投影选择等）	2



C:\Users\Administrator\OneDrive\prjbek fixt1109\platform-top-service1109pm\platform-top-service\platform-top-service-finance\src\main\java\org\chwin\firefighting\apiserver\dsl\spelUtil.java



   ExpressionParser parser = new SpelExpressionParser();

        Expression exp = parser.parseExpression("new org.chwin.firefighting.apiserver.dsl.lombokTest().m1()");

        System.out.println(exp.getValue());
     

特别注意Spel 调用静态方法是这样的t（）把静态类抱起里

/T(com.kok.sport.utils.CaptchData).m1()
