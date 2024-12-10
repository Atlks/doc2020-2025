Atitit hot deploy 热部署法  dync reload v5 v55



Script引擎法
Debug模式启动 推荐
如果JVM运行时开启JPDA（Java Platform Debugger Architecture），则Class是运行被动态重新载入的。具体方式可以参考java.lang.Instrument。javassist也提供了一个运行期重载Class的方法，具体可以看API 中的javassist.tools.HotSwapper。
新增加方法也支持reload类。。Jdk8
$java -agentlib:hprof=help 用来性能分析。。
-agentlib:jdwp=transport=dt_socket,suspend=y,address=localhost:54367

 Java Debug Wire Protocol (JDWP) is v

package util;

import java.util.Date;
import java.util.concurrent.TimeUnit;

public class DynClass {
	
	public static void main(String[] args) throws  Exception {
		while(true)
		{
			System.out.println(PayUtil.h()+new Date());
			TimeUnit.SECONDS.sleep(5);
		}

	}
	
	
}
Springboot 热部署jar工具 dev tools
Mybatis reload sqlfactory
多个mybatis Cfg
Invoke script php js法cli
Other
Cmd reload sdk法

使用javaassit动态加载classloader工具
热部署  crontab kill and restart
Ps -ef ,,batch kill   by path

5分钟生效  20分钟等

使用jsp 

使用其他



Atitit node express 热更新解决方案 热部署 修改不生效解决方案
Atitit.软件仪表盘(17）-----热部署jrebel 5.5.2 的使用
