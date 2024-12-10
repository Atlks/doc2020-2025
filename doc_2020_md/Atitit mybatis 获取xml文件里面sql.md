Atitit mybatis 获取xml文件里面sql


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
