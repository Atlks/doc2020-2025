Atitit sprbt test  code exmp



package sprbtPKg;

import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.junit4.SpringRunner;

/**
 * import org.springframework.boot.test.context.SpringBootTest; from sprigoot  tests
import org.springframework.test.context.junit4.SpringRunner; from  spring test
 * 
 * @author user
 *
 */
@RunWith(SpringRunner.class)
@SpringBootTest(classes = { Application.class }) // ָ��������
public class SpringbootTest {
	
	public static void main(String[] args) {
		
	}

	// @SpringApplicationConfiguration(classes = Application.class)// 1.4.0 ǰ�汾
	@Autowired
	 HelloController hc;

	@Test
	public void testOne() {
		System.out.println(""+hc.hello());
	}

}




package sprbtPKg;


/*
 * */

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.builder.SpringApplicationBuilder;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
 
 
@SpringBootApplication
public class Application   {
 
//  protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
//      return application.sources(Application.class);
//  }
 
  public static void main(String[] args) throws Exception {
      SpringApplication.run(Application.class, args);
      
      
      
      
  }
  
  
  @Configuration
 
  @ComponentScan(lazyInit = true)
  static class LocalConfig {
  }
}


  
  <!--  sprbt start  -->
	<!--  sprbt start  need part.. nood def any springt ver in perperties and jackson ver -->
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		  <version>2.2.6.RELEASE</version>
	</parent>
	
	<dependencies>
	
		
	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		
		<!-- 
	 springboot test
		 -->
		
			<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-test</artifactId>
			<version>5.2.5.RELEASE</version>
		</dependency>	
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-test</artifactId>
			<scope>test</scope>
		</dependency>
		
			<!-- 
	 springboot test   end
		 -->
	<!--  sprbt end -->
