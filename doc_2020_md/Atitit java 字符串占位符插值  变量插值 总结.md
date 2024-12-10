Atitit java 字符串占位符插值  变量插值 总结


java字符串占位符MessageFormat.format(args1, args2…)；

MessageFormat.format(args1, args2…)；
第一个参数是含有占位符的字符串，第二个参数是一个可变参数，相当于一个数组，对应于占位符里面的数字，
举个例子

 String message = MessageFormat.format("我是{0}，我来自{1}", "中国人", "中国");

        System.out.println(message);
1
2
3
结果：
我是中国人，我来自中国

参数列表的类型是Object，所以任何类都可以，比如，Date，会调用toString()方法替换占位符内容

占位符{number}，number可以不从0开始，也可以重复，会对应后面可变参数相对应位置。

若占位符数量多于可变参数的数量，多余的占位符不会替换，原样显示占位符，比如，{3}

占位符可以不按照顺序写，比如，先写{1}，在写{0}

MessageFormat是从jdk1.5加入的，所以jdk不能是之前版本的
————————————————
版权声明：本文为CSDN博主「zhaodeng_2017」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/zhaodeng_2017/article/details/75043851
JAVA字符串格式化-String.format()的使用
原创LeeFranker 最后发布于2012-09-10 11:01:10 阅读数 912547  收藏
展开
常规类型的格式化

String类的format()方法用于创建格式化的字符串以及连接多个字符串对象。熟悉C语言的同学应该记得C语言的sprintf()方法，两者有类似之处。format()方法有两种重载形式。

format(String format, Object... args) 新字符串使用本地语言环境，制定字符串格式和参数生成格式化的新字符串。

format(Locale locale, String format, Object... args) 使用指定的语言环境，制定字符串格式和参数生成格式化的字符串。

显示不同转换符实现不同数据类型到字符串的转换，如图所示。


转  换  符

说    明 

示    例

%s

字符串类型


Spel velocity
