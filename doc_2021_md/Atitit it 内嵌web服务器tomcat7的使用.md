Atitit it 内嵌web服务器tomcat7的使用

C:\Users\Administrator\eclipse-workspace\tomcat7embd


		// jsp support  and htm suport already

package tomcat7embd;

import org.apache.catalina.Context;
import org.apache.catalina.LifecycleException;
import org.apache.catalina.startup.Tomcat;

public class start {

	//TomcatV6U66
		public static void main(String[] args) throws LifecycleException {
			
			System.out.println("-start");
			
			Tomcat tomcat=new Tomcat();	
			tomcat.setPort(8080);
			
			
			//set basedir
		 	String basedir = "C:\\Users\\Administrator\\eclipse-workspace\\tomcat7embd\\basedirTomcat";
			 tomcat.setBaseDir(basedir);	
			Context Context1_Webapp=	tomcat.addWebapp("/", basedir);//addWebapp()过时了		
			
			
			
			
			//--------add svlt rest api
			
			String servletName = "servletName";
			tomcat.addServlet(Context1_Webapp, servletName,  new MvcServlet());
			Context1_Webapp.addServletMapping("/halo",servletName);//配置servlet映射路径
			
			
			// jsp support  and htm suport already
			
			
			//start
			tomcat.start();
			tomcat.getServer().await();
			System.out.println("f");
		}
}





<dependencies>

		<!-- https://mvnrepository.com/artifact/org.apache.tomcat.embed/tomcat-embed-core -->
		<dependency>
			<groupId>org.apache.tomcat.embed</groupId>
			<artifactId>tomcat-embed-core</artifactId>
			<version>7.0.107</version>
		</dependency>


		<!-- https://mvnrepository.com/artifact/org.apache.tomcat/juli -->
		<dependency>
			<groupId>org.apache.tomcat</groupId>
			<artifactId>juli</artifactId>
			<version>6.0.53</version>
		</dependency>
		
		
		<!-- https://mvnrepository.com/artifact/org.apache.tomcat/jasper -->
<dependency>
    <groupId>org.apache.tomcat</groupId>
    <artifactId>jasper</artifactId>
    <version>6.0.53</version>
</dependency>
		


	</dependencies>
