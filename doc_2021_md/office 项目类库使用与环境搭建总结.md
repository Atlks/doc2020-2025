Ule office 项目类库使用与环境搭建总结

类库依赖管理
没有使用maven模式，直接配置ide引入web-inf/lib的jar即可。

源码src
有时候不在ide源码管理里面，需要设置为source文件夹。。

##Mvc类库
Struts2
Spring2.5.6   vue2.x

###Orm   
hibernate  springjdbc

部署与启动
需要在ide里面tomcat插件上面配置下。。
更加方便快捷的方式是以springboot模式内嵌tomcat启动法，免配置,报错也更加详细
目前tomcat用的版本是v7.0.x


访问
Localhost:8080/




