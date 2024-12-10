Atitit 接口异常处理法

异常模式下返回异常的json序列化

指标需要返回errcode等
需要返回context信息

实现方法  
组合法，返回一个map，使用e，errcode，context组合比较好。。。
新继承一个ex类



Map m = Maps.newLinkedHashMap();
m.put("e", e);
m.put("errcode", 111);
String s = JSON.toJSONString(m, true);
return s;


{
	"@type":"java.lang.RuntimeException",
	"localizedMessage":"ex:cantfind_cookie,cookiename:curUserInfo.uname",
	"message":"ex:cantfind_cookie,cookiename:curUserInfo.uname",
	"stackTrace":[{
		"className":"org.chwin.firefighting.apiserver.data.CookieUtil",
		"fileName":"CookieUtil.java",
		"lineNumber":43,
		"methodName":"getValue",
		"nativeMethod":false
	},{
		"className":"org.chwin.firefighting.apiserver.data.DataContrler",
		"fileName":"DataContrler.java",
		"lineNumber":86,
		"methodName":"executeSp",
		"nativeMethod":false
	},{

返回码定义  数字与字母型返回码
