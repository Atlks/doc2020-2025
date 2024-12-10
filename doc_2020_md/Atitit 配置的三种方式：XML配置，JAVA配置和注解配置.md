Atitit 配置的三种方式：XML配置，JAVA配置和注解配置


//JAVA配置
@Confirguration 相当于spring的配置文件XML
@Bean 用到方法上，表示当前方法的返回值是一个bean
1
2
3
这两种方法的区别在于如果使用注解的方式，那么你需要在Serivce层，DAO层的时候，需要在类上进行注解，就可获得spring的依赖注入：


如果使用java配置的方式，那么就不需要在类上写注解了，直接在配置类里面进行申明即可：

package javaconfig;
 
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
 
@Configuration
public class JavaConfig {
    //通过这种方式，获得spring的依赖注入
    @Bean
    public UseFunctionService useFunctionService () {
        return new UseFunctionService ();
    }



这两种方式没有什么所谓的优劣之分，主要看使用情况，一般来说是这样：
涉及到全局配置的，例如数据库相关配置、MVC相关配置等，就用JAVA配置的方式
涉及到业务配置的，就使用注解方式

