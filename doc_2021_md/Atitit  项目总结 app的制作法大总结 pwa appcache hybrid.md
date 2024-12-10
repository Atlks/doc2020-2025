Atitit  项目总结 app的制作法大总结


Atitit  项目总结 app的制作法大总结 pwa appcache hybrid

原生与
hybrid
appcache 
但实现了cache离线app
没有安装图标，可以使用浏览器快捷方式来实现

需要针对每一个url做书写，不能像pwa一样编程动态cache，代码量大


没有后台进程

appcache 问题是无法实现net first缓存策略。。


pwa 
初步安装可以不用很多url，，逐步cache ui即可。。
数据请求 方便net firts cache策略实现。。
有通知实现，但通知比较麻烦，可能使用stom socket协议更加简单些。。
