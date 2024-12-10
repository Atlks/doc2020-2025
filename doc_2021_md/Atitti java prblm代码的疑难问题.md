Atitti java prblm代码的疑难问题

找不到类问题

.NoClassDefFoundError: org.springframework.beans.FatalBeanException
调整xss xmx等参数。。动态加载类太多了，爆了

提前syso  class 提前在main里面ref

不能但不debug
卡住对情况。。
找不到类，但run就可以。。

不是自己想要的结果
可能是加载了过时对class。。增加一个satic 变量，强制首先引用下，预先load
轻质加载jar预先。。

查看ide error maven update解决
