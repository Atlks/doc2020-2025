Atitit mybatis Invalid bound statement (not found)

	//	org.slf4j.impl.StaticLoggerBinder.getSingleton();
		Map<String,String> map =new HashMap<String, String>();
		map.put("username", "admin");
		map.put("password", "admin");
		 UsersMapper usersMapper=  SpringUtil.build4wash().getBeanV2(UsersService.class);
		List<Users> list = usersMapper.QueryByUsersByMap(map);
		System.out.println(AtiJson.toJson(list));
		System.out.println("f");



Exception in thread "main" org.apache.ibatis.binding.BindingException: Invalid bound statement (not found): com.taYu.dao.UsersMapper.QueryByUsersByMap
	at org.apache.ibatis.binding.MapperMethod$SqlCommand.<init>(MapperMethod.java:184)
	at org.apache.ibatis.binding.MapperMethod.<init>(MapperMethod.java:38)
	at org.apache.ibatis.binding.MapperProxy.cachedMapperMethod(MapperProxy.java:49)
	at org.apache.ibatis.binding.MapperProxy.invoke(MapperProxy.java:42)
	at com.sun.proxy.$Proxy65.QueryByUsersByMap(Unknown Source)


刚刚解决了这个问题，比如有一个UserDao，你就必须命名为UserDao.xml，我是因为这个困扰了好久


@Repository(value="userMapper")
public interface UserMapper {
    public List<User> getAll();
}

下面是userMapper.xml
<mapper namespace="com.yolly.platform.user.mapper.UserMapper">
    <select id="getAll" resultType="user">
        select * from user
    </select>
</mapper>

这里红色标注的两个地方属性名称要一致 ，要不就会出现（not fond ）的情况！！！！



@Autowired
public void setUserService(UserService userService) {
this.userService = userService;
}
应该是这里错了啊

用@Resource byName来注入啊

下面是完整的解释
@Resource的作用相当于@Autowired，只不过@Autowired按byType自动注入，而@Resource默认按 byName自动注入罢了。@Resource有两个属性是比较重要的，分是name和type，Spring将@Resource注解的name属性解析为bean的名字，而type属性则解析为bean的类型。所以如果使用name属性，则使用byName的自动注入策略

