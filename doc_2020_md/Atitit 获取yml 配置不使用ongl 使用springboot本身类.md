Atitit 获取yml 配置不使用ongl 使用springboot本身类

7月份23工作日，，25--31 五个wd,一个ot..
加载 application.yml 文件

YamlPropertiesFactoryBean yamlMapFactoryBean = new YamlPropertiesFactoryBean();
//可以加载多个yml文件
yamlMapFactoryBean.setResources(new ClassPathResource("application.yml"));
Properties properties = yamlMapFactoryBean.getObject();

//获取yml里的参数
String active = properties.getProperty("spring.profiles.active");
System.out.println("active:"+active);


SpringBoot 不依赖注入获取 application.yml 参数 - 黑客派.html

