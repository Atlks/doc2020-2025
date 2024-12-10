Atitit xml解析总结

先验货dom4j但是mven胡，运行  这个有点老2006年颁布最新
aaa=1&amp;bbb=2
Exception in thread "main" java.lang.NoClassDefFoundError: org/jaxen/JaxenException
	at org.dom4j.DocumentFactory.createXPath(DocumentFactory.java:230)
	at org.dom4j.tree.AbstractNode.createXPath(AbstractNode.java:207)
	at org.dom4j.tree.AbstractNode.selectNodes(AbstractNode.java:164)
	at com.kok.sport.utils.XmlUtilAti.main(XmlUtilAti.java:44)
Caused by: java.lang.ClassNotFoundException: org.jaxen.JaxenException
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	... 4 more


使用jdom 2008
<dependency>
    <groupId>jdom</groupId>
    <artifactId>jdom</artifactId>
    <version>1.1</version>
</dependency>


结果xmpath都需要这个jaxen


    <dependency>
    <groupId>jaxen</groupId>
    <artifactId>jaxen</artifactId>
    <version>1.2.0</version>
</dependency>


XPath 语法

      //  com.sun.org.apache.xml.internal.security.utils.XMLUti
    String xmlf = "D:\\prj\\sport-service\\kok-sport-service\\src\\main\\resources\\mapper\\FootballLiveMatchdetailliveDao.xml";
    String xpath = "/update";  
    //jdom
    SAXBuilder sb=new SAXBuilder();
    org.jdom.Document doc=sb.build(xmlf);
    Element root=(Element) doc.getRootElement();
String pathFltById = "//*[@id='insert_into_football_incident_t']/text()";
Object sql=((Text)XPath.selectSingleNode(root,pathFltById)).getValue();
   // doc./tex
