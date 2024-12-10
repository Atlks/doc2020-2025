Atitit   UrlResource url协议路径  


URL to load resources from the classpath in Java
在Java中，您可以使用相同的API，但使用不同的URL协议来加载各种资源：
这很好地将资源的实际加载与需要资源的应用程序分离开来，并且由于URL只是一个字符串，因此资源加载也很容易配置


4.2.5 UrlResource
UrlResource代表URL资源，用于简化URL资源访问。“isOpen”永远返回false，表示可多次读取资源。
UrlResource一般支持如下资源访问：
http：通过标准的http协议访问web资源，如new UrlResource(“http://地址”)；
ftp：通过ftp协议访问资源，如new UrlResource(“ftp://地址”)；
file：通过file协议访问本地文件系统资源，如new UrlResource(“file:d:/test.txt”)；
具体使用方法在此就不演示了，可以参考cn.javass.spring.chapter4.ResourceTest中urlResourceTest测试方法。

		// String mapPath = "classpath:mapper/**/*.xml";
