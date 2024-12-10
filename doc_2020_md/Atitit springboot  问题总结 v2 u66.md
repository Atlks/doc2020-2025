Atitit springboot  问题总结t0015


Def use cfg  file by 

spring:
  profiles:
    active: '@profileActive@'

Pom.xm
 <!--定义打包命令指定的环境对应的profileActive变量值-->
    <profiles>
        <profile>
            <id>dev</id>
            <properties>
                <profileActive>prod</profileActive>
            </properties>
            <activation>
                <!--指定默认激活-->
                <activeByDefault>true</activeByDefault>
            </activation>
Datasource url
Could not resolve placeholder 'spring.application.name' in value "${spring.application.name}"



Add cfg


spring:
  application:
    name: xxxx



SpringBoot发布打包动态切换环境

我本佛山人关注
2017.09.07 09:22:19字数 304阅读 1,225
SpringBoot支持多种方式切换环境配置信息，如在配置文件中配置spring.profiles.active: dev，则表明加载application-dev.yml，但这种方式是写死在配置文件中的，一般在发布项目时需在命令行下根据指定环境动态改变spring.profiles.active的值，针对这种方式如我们使用的是MAVEN打包工具，可通过如下方式来改变。

