Atitit 多环境配置解决方案

配置文件本身支持多环境模式，，springboot ,,,mybatis里面对数据源切换



通过cmd 参数指定配置文件路径 更好

Mysql也是这样制定配置文件路径

java -jar xxxxx.jar --spring.config.location=/opt/conf/application.properties

Maven配置多环境srping项目也是这样制定的

这样就可以了。 然后使用maven打包时，使用：mvn package -P online，就可以打生产包了。
