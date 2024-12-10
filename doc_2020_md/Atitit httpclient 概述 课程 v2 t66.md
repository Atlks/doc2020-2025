Atitit httpclient 概述  rest接口



Httpclient 利用http协议的client类库与技术方法

Get post 方法

http server  ：：java servlet

功能用途 why
上传下载文件
 文本html  ；爬虫采集
提交表单等
具体流程how
连接httpserver ，接受字节流，如果是文本，可能需要转码(gbk utf）为字符串

传入一个url，得到输出值html json

跨语言Cli模式 curl的使用
 "D:\\prgrm\\bin\\curl.exe  http://localhost:8088/list.json";	
		
 主义默认curl使用gbk编码读取。。所以url输出要是gbk
或者使用iconv转换编码 not ati tested.
curl http://www.baidu.com | iconv -f gb2312 -t utf-8 iconv
不同语言与环境下的使用 api模式
Java httpclient

// 执行get请求.
		CloseableHttpResponse response = HttpClients.createDefault().execute(new HttpGet(url));
		// 获取响应实体
		String html = EntityUtils.toString(response.getEntity());
		return html;
Python  
Js 浏览器环境ajax

Js node环境 http模块
跨语言curl工具
Php 
Net 的httpclient

Python的实现
import urllib.request 报错 ，貌似对gzip支持不好


from bs4 import BeautifulSoup, Comment
import urllib.request
import requests
response = urllib.request.urlopen('http://www.qq.com/')
##html = response.read().decode('UTF-8','ignore')
#html = response.read().decode('gb2312','ignore')
# print (html)

使用 requests模块 即可

r = requests.get('http://www.qq.com/')

print(r.text)



Rf
Atitit python获取html源码

