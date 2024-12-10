atitit mvc的使用总结v3
 

mvc框架有  xxp模式（jsp php aspx等），tp springmvc struts, vue等。
项目中用到的有struts,springmvc,vue这三个mvc框架


#注册总体拦截器

一搬根据拦截扩展名判断，mime内容注册机制，不同的扩展名使用不同的mvc框架拦截解析
  也有根据前缀路径判断的
##Xxp模式是约定大于配置模型，不需要特殊实现
##Struts设置
 web.xml中添加如下代码，拦截对应的请求， 
<filter>
 <filter-name>struts</filter-name>
 <filter-class>org.apache.struts2.dispatcher.ng.filter.StrutsPrepareAndExecuteFilter</filter-class> </filter>
 <filter-mapping> 
<filter-name>struts</filter-name> <url-pattern>/*.do</url-pattern> </filter-mapping>

##springmvc2.5.6
<!--spr mvc cfg name just same with this svltname -->
  <servlet>
     <servlet-name>spring-mvc-dispatcher</servlet-name>
     <servlet-class>
        org.springframework.web.servlet.DispatcherServlet
     </servlet-class>
     <load-on-startup>1</load-on-startup>
  </servlet>

  <servlet-mapping>
     <servlet-name>spring-mvc-dispatcher</servlet-name>
     <url-pattern>*.spr</url-pattern>
  </servlet-mapping>

Note::Spring2.5.6 有bug不兼容jdk8 ,需要小调整
## springmvc2.5兼容Jdk8补丁修正
<!--spr mvc v100 for jdk8-->

<servlet>
  <servlet-name>spring-mvc-dispatcherV100</servlet-name>
  <servlet-class>
     org.springframework.web.servlet.DispatcherServletV100
  </servlet-class>
  <load-on-startup>1</load-on-startup>
</servlet>

<servlet-mapping>
  <servlet-name>spring-mvc-dispatcherV100</servlet-name>
  <url-pattern>*.ati</url-pattern>
</servlet-mapping>


Vue的配置
// 2. 定义路由 客户端hash 路由
//vue-router 默认 hash 模式 —— 使用 URL 的 hash 来模拟一个完整的 URL，于是当 URL 改变时，页面不会重新加载。另外一种使用h5 history模式
 //  file:///D:/xxx.html#/bar
const routes = [
    { path: '/foo', component: { template: '<div>foo............</div>' } },
    { path: '/bar', component:  { template: '<div>bar...................</div>' } }
]
 

var Vue1 = new Vue({
  /*
router: new VueRouter({
    routes // （缩写）相当于 routes: routes
})
,
*/
  el: '#app',
  data: {
    message: 'Hello Vue!',objlist:[],userlist:[]
  }
})


#注册请求url与对应的响应代码块

Xxp模式是约定大于配置模型，不需要特殊实现，使用url路径直接对应
Struts需要在struts.xml里面去配置  url与java代码块方法对应关系

 <action name="xxxapi" class="xx" method="mtd2"></action>


Springmvc在其配置文件配置也是或者注解扫描实现

Vue也需要类似的配置
const routes = [
    { path: '/foo', component: { template: '<div>foo............</div>' } },
    { path: '/bar', component:  { template: '<div>bar...................</div>' } }
]



使用配置url请求表映射，url映射方法引用，或使用反射法，或使用动态调用代码法

设置显示范围 路由出口渲染
后端mvc默认显示到所有。需要配置头跨域。。。如需要设置显示范围，也可特定json标签指明

Vue配置
 <!-- 路由出口 -->
  <!-- 路由匹配到的组件（代码块）将渲染在这里 -->
  <router-view></router-view> 



