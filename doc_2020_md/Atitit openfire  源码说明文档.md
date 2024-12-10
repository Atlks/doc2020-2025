Atitit openfire  源码说明文档

出改变
==============
该项目使用[Maven]（https://maven.apache.org/），因此应直接导入您喜欢的Java IDE。
目录结构非常简单。主要代码包含在：

*`Openfire / xmppserver`-一个Maven模块，代表Openfire本身的核心代码

其他文件夹是：
*`Openfire / build`-各种文件用于为不同平台创建安装程序
*`Openfire / distribution`-一个Maven模块，用于将所有零件组合在一起
*`Openfire / documentation`-托管在[igniterealtime.org]（https://www.igniterealtime.org/projects/openfire/documentation.jsp）上的文档
*`Openfire / i18n`-用于管理界面国际化的文件
*`Openfire / plugins`-Maven配置文件，以允许构建各种[plugins]（https://www.igniterealtime.org/projects/openfire/plugins.jsp）
*`Openfire / starter`-一个小模块，允许Openfire在不同平台上以一致的方式启动

要构建包括插件的完整项目，请运行以下命令
```
./mvnw验证
```

但是，在大多数情况下，仅需要对核心XMPP服务器本身进行更改，在这种情况下，该命令
```
./mvnw验证-pl分发-am
```
将编译核心服务器及其任何依赖项，然后将其组装成可以运行的东西。
To build the complete project including plugins, run the command
./mvnw verify
However much of the time it is only necessary to make changes to the core XMPP server itself in which case the command
./mvnw verify -pl distribution -am 
will compile the core server and any dependencies, and then assemble it in to something that can be run.


测试您的更改
--------------------

#### IntelliJ IDEA：

1.运行->编辑配置...->添加应用程序
2.填写以下值
    1.名称：Openfire
    2.使用模块的类路径：启动器
    3.主类：org.jivesoftware.openfire.starter.ServerStarter
    4. VM选项（相应调整）：
        ``
        -DopenfireHome =“-项目文件夹的绝对路径-\ distribution \ target \ distribution-base”
        -Xverify：无
        -服务器
        -Dlog4j.configurationFile =“-项目文件夹的绝对路径-\ distribution \ target \ distribution-base \ lib \ log4j2.xml”
        -Dopenfire.lib.dir =“-项目文件夹的绝对路径-\ distribution \ target \ distribution-base \ lib”
        -Dfile.encoding = UTF-8
       ``
   5.工作目录：-项目文件夹的绝对路径-
3.申请




#### IntelliJ IDEA:

1. Run -> Edit Configurations... -> Add Application
2. fill in following values
    1. Name: Openfire
    2. Use classpath of module: starter
    3. Main class: org.jivesoftware.openfire.starter.ServerStarter
    4. VM options (adapt accordingly):
        ````
        -DopenfireHome="-absolute path to your project folder-\distribution\target\distribution-base" 
        -Xverify:none
        -server
        -Dlog4j.configurationFile="-absolute path to your project folder-\distribution\target\distribution-base\lib\log4j2.xml"
        -Dopenfire.lib.dir="-absolute path to your project folder-\distribution\target\distribution-base\lib"
        -Dfile.encoding=UTF-8
       ````
Working directory: -absolute path to your project folder-


Ui jsp路径

C:\opf\Openfire\xmppserver\src\main\webapp\login.jsp

正式版可能在jar里面看不到jsp



您需要先执行mvnw verify才能启动openfire。
其他IDE：
尽管您的IDE可以愉快地编译项目，但是不幸的是，无法在IDE中运行Openfire-必须在命令行中完成。使用Maven构建项目后，只需运行shell脚本或批处理文件以启动Openfire；
./distribution/target/distribution-base/bin/openfire.sh
要么
.\distribution\target\distribution-base\bin\openfire.bat
将-debug第一个参数添加为脚本将以调试模式启动服务器，并且在必要时您的IDE应该能够连接远程调试器。

