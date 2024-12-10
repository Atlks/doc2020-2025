Atitit   注解的使用 建立  设置与读取流程


注解的使用
注解定义

package ref;

import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;

@Retention(RetentionPolicy.RUNTIME)
public @interface 我的注解 {

	String 属性();

	String 属性2();

}
注解设置使用
 @我的注解(属性="111",属性2="2222")
public class UserService {


注解读取
	Class cls=	UserService.class;
	我的注解   anno1=  (我的注解) cls.getAnnotation(我的注解.class);
	System.out.println(anno1.属性());
	System.out.println(anno1.属性2());

