Atitit java项目常用类库表




Ati总的常用库
表达式，语言解析类库
commons-cli-1.4
Beanshell bsh  bsh-core-2.0b4
Ognl库  groovy库
字符串模板解析库velocity freemark
 rest库  javax。Ws
javax.ws.rs-api-2.1
存储类的库  mongodb，dbutil

其他20库
日志相关类库
二、JSON解析库 三、单元测试库
四、通用类库
有几个很好的第三方通用库可供Java开发人员使用，例如Apache Commons和Google Guava
五、Http 库
我不是很喜欢JDK的一个重要原因就包括他们缺乏对HTTP的支持。虽然可以使用java.net包类，但是这和直接使用像Apache HttpClient和HttpCore等开源类库比起来麻烦太多了
八、字节码库
如果你正在编写一个框架或者类库。有一些受欢迎的字节码库如javassist和Cglib Nodep可以供你选择，他们可以让你阅读和修改应用程序生成的字节码。
十三、集合类库
虽然JDK有丰富的集合类，但还是有很多第三方类库可以提供更多更好的功能。如Apache Commons Collections、 Goldman Sachs collections、 Google Collections和Trove。Trove尤其有用，因为它提供所有标准Collections 类的更快的版本以及能够直接在原语（primitive）（例如包含int 键或值的Map 等）上操作的Collections 类的功能。
FastUtil是另一个类似的API，它继承了Java Collection Framework，提供了数种特定类型的容器，包括映射map、集合set、列表list、优先级队列（prority queue），实现了java.util包的标准接口（还提供了标准类所没有的双向迭代器），还提供了很大的（64位）的array、set、list，以及快速、实用的二进制或文本文件的I/O操作类。

十五、HTML解析库
和XML与JSON类似，HTML是另外一种我们可能要打交道的传输格式。值得庆幸的是，我们有jsoup可以大大简化Java应用程序使用HTML。你不仅可以使用JSoup解析HTML还可以创建HTML文档。
十七、嵌入式SQL数据库库
我真的是非常喜欢像H2这种内存数据库，他可以嵌入到你的Java应用中。在你跑单测的时候如果你需要一个数据库，用来验证你的SQL的话，他是个很好的选择。顺便说一句,H2不是唯一嵌入式DB，你还有Apache Derby和HSQL可供选择。
十八、JDBC故障诊断库 P6Spy 
有不错的JDBC扩展库的存在使得调试变得很容易，例如P6spy，这是一个针对数据库访问操作的动态监测框架，它使得数据库数据可无缝截取和操纵，而不必对现有应用程序的代码作任何修改。P6Spy 分发包包括P6Log，它是一个可记录任何 Java 应用程序的所有JDBC事务的应用程序。其配置完成使用时，可以进行数据访问性能的监测。
二十、网络库
 



Java开发人员必知必会的20种常用类库和API.mhtml
