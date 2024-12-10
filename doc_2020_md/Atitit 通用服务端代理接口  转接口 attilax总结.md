Atitit 通用服务端代理接口  转接口 attilax总结

1.1. 主要使用场景： 强行跨域，方便界面与后端的数据调用	1
1.2. 原理：使用httpclient转发接口数据。	1
1.3. 注意：：元接口的数据编码最好不用动，直接stream转换。。	1
1.4. 大概流程与算法	1
1.5. 核心代码	2
1.6. 范例与使用说明，天气接口，需要使用本地html文件读取其他域名的rest api	4


目前我们自己的 通用接口基本可以满足数据查询，数据更新删除的这些场合了，甚至可以做到主要靠前端人员就可以做很多项目了（还缺少一个通用excel导出功能）。。
但面对别人提供的接口，还需要做一些转换。。因为默认html ajax是读取不了第三方域名地址的接口的。

主要使用场景： 强行跨域，方便界面与后端的数据调用
对方给的接口没有跨域设置。导致不能直接在界面使用。。
优先让对方开通跨域设置。。如果不能开通，比如第三方接口，或者对方不愿意开通此设置。

就需要使用服务端代理做个转接口。。

原理：使用httpclient转发接口数据。

注意：：元接口的数据编码最好不用动，直接stream转换。。
未来版本规划：：： 支持编码转换 gbk utf8等。
支持

大概流程与算法
/Proxy.java 入口
HttpUtil发送http请求
然后stream交换
核心代码
/atiplat_ee/src/com/attilax/rest/Proxy.java

	}

/atiplat_ee/src/com/attilax/net/HttpUtil.java



/atiplat_ee/src/com/attilax/io/StreamUtil.java



范例与使用说明，天气接口，需要使用本地html文件读取其他域名的rest api
http://www.weather.com.cn/data/cityinfo/101250101.html

返回
{"weatherinfo":{"city":"长沙","cityid":"101250101","temp1":"11℃","temp2":"22℃","weather":"多云","img1":"n1.gif","img2":"d1.gif","ptime":"18:00"}}

转接口使用
http://localhost:8088/proxy?url=http%3A%2F%2Fwww.weather.com.cn%2Fdata%2Fcityinfo%2F101250101.html

提供一个url参数，指明原接口的url即可。。注意莫忘urlencode


返回
{"weatherinfo":{"city":"长沙","cityid":"101250101","temp1":"11℃","temp2":"22℃","weather":"多云","img1":"n1.gif","img2":"d1.gif","ptime":"18:00"}}


