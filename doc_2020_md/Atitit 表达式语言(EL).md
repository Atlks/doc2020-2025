Atitit 表达式语言(EL)


Java - 表达式语言(EL)
表达式语言(Expression Language)简称EL，它是JSP2.0中引入的一个新内容。通过EL可以简化在JSP开发中对对象的引用，从而规范页面代码，增加程序的可读性及可维护性。EL为不熟悉Java语言页面开发的人员提供了一个开发Java Web应用的新途径。下面对EL的语法、运算符及隐含对象进行详细介绍。

3、保留的关键字
       EL中保留的关键字如下，在为变量命名时，应该避免使用这些关键字：
二、EL的运算符使用

       EL的运算符在按照从左向右的计算原则下，优先级如下：

三、EL的隐含对象
       为了能够获得Web应用程序中的相关数据，EL提供了11个隐含对象，这些对象类似于JSP的内置对象，也是直接通过对象名进行操作。
1、页面上下文对象
       pageContext用于访问JSP内置对象和servletContext。在获取到这些内置对象后，就可以获取器属性值。这些属性与对象的gexxx()方法相对象，在使用时，去掉方法名中的get，并将首字母改为小写即可。下面介绍如何应用页面上下文对象访问你JSP的内置对象和servletContext对象。
       1)、访问request对象——${pageContext.request}
       获取到request对象后，就可以通过该对象获取与客户端相关的信息。例如要访问getServerPort()方法，可以使用下面的代码：
       ${pageContext.request.serverPort}
       注意不可以通过pageContext对象获取保存到request范围内的变量。
       2)、访问response对象——${pageContext.response}
       3)、访问out对象——${pageContext.out}
       4)、访问session对象——${pageContext.session}
       5)、访问exception对象——${pageContext.exception}
       6)、访问page对象——${pageContext.page}
       7)、访问servletContext对象——${pageContext.servletContext}
2、访问作用域范围的隐含对象
       在EL中提供了4个用于访问作用域范围的隐含对象，即pageScope、requestScope、sessionScope和applicationScope。应用这4个隐含对喜爱那个指定要查找的标识符的作用域后，
3、访问环境信息的隐含对象
       EL中提供了6个访问环境信息的隐含对象，分别为：
       1)、param对象
  2)、paramValues对象
       如果一个请求参数名对应多个值，则需要使用paramValues对象获取请求参数的值，该对象返回的结果为数组。例如：
  3)、header和headerValues对象
       用于获取HTTP请求的一个具体的header值，当同一个header存在多个值时需使用headerValues对象。例如：
       ${header[“connection”]}获取HTTP请求的header的是否需要持久连接这一属性
       4)、initParam对象
       用于获取Web应用初始化参数的值。例如：
       在web.xml文件中设置一个初始化参数user：
              <context-param>
                   <param-name>user</param-name>
                   <param-value>小武</param-value>
            </context-param>
       使用EL获取该参数：
              ${initParam.user}
       5)、cookie对象
       用于访问由请求设置的cookie。例如
四、定义和使用EL函数
       EL允许定义和使用函数，但是eclipse好像不能自动生成tld文件，我嫌麻烦，而且EL函数不常用，所以这里不介绍了。

