Spring注解区别 Component  Controller Service Repository    

@Component 通用，简单易用
@Controller  @Service Repository    优点 清晰明了
 

@Component /** 注册为spring的组件bean **/
@Controller
@Service
@org.springframework.stereotype.Repository    /** dao层 **/
public class BeanOne {

	public String outputHH(String string) {
		// TODO Auto-generated method stub
		return "HHH";
	}

使用场合 
快速简单类型的用Component 
大型复杂的使用Controller  
