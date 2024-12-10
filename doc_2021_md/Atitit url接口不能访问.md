Atitit url接口不能访问

看是不是有拦截器阻挡

implements HandlerInterceptor



import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurationSupport;

/**
 * 注册拦截器
 * 
 * @author acan
 * @date 2020年4月26日
 * @version 1.0
 */
@Configuration
public class InterceptorConfig extends WebMvcConfigurationSupport {
