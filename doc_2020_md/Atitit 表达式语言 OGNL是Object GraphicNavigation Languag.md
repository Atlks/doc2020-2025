Atitit 表达式语言 OGNL是Object GraphicNavigation Language（对象图导航语言）概述


OGNL是Object GraphicNavigation Language（对象图导航语言）的缩写，OGNL是一个开源项目，读者可以访问其官方站点www.ognl.org以获得源代码和相关资料。OGNL是一种功能强大的EL（Expression Language，表达式语言），可以通过简单的表达式来访问Java对象中的属性。本节为您介绍OGNL的优势。

使用OGNL是非常简单的，如果要访问的对象不是根对象，如示例中的bar对象，则需要使用命名空间，用“#”来标识，如“#bar”；如果访问一个根对象，则不用指定命名空间，可以直接访问根对象的属性。


8.2.2  OGNL的集合操作
如果需要一个集合元素的时候（例如List对象或者Map对象），可以使用OGNL中同集合相关的表达式。
可以使用如下代码直接生成一个List对象：
该OGNL表达式中，直接生成了一个List对象，该List对象中包含3个元素：e1、e2和e3。如果需要更多的元素，可以按照这样的格式定义多个元素，多个元素之间使用逗号隔开。
如下代码可以直接生成一个Map对象：

Map类型的集合对象，使用key-value格式定义，每个key-value元素使用冒号标识，多个元素之间使用逗号隔开。
对于集合类型，OGNL表达式可以使用in和not in两个元素符号。其中，in表达式用来判断某个元素是否在指定的集合对象中；not in判断某个元素是否不在指定的集合对象中，如代码8.3所示。
8.2.3  Lambda表达式
OGNL支持基本的Lambda表达式语法，通过Lambda表达式语法，可以在OGNL中使用一些简单的函数。例如：
8.3.4  OGNL中的#、%和$符号
#、%和$符号在OGNL表达式中经常出现，而这三种符号也是开发者不容易掌握和理解的部分。在这里笔者简单介绍它们的相应用途。

1．#符号
#符号的用途一般有三种。
 
访问非根对象属性，例如示例中的#session.msg表达式，由于Struts 2中值栈被视为根对象，所以访问其他非根对象时，需要加#前缀。实际上，#相当于ActionContext. getContext()；


竞争对手 mvel
老牌的Ognl(老到网站都找不到了) 新来的MVEL 国产的Aviator 目前最快的JSEL:JSEL测试表达式: ...



8.1.1 OGNL的优势 - 51CTO.COM.mhtml
《Struts 2技术详解：基于WebWork核心的MVC开发与实践》第8章主要讲的是OGNL
