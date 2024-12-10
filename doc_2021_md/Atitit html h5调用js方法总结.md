Atitit html h5调用js方法总结


直接使用《script》标签内嵌，适用于 page加载

在一些HTML控件的事件属性中使用（一般事件为onxxx

，如onmouseover,onclick,onchange）

< body  onload ="alert('loaded');" >
< input  type ="text"  name ="username"  onclick ="alert(this.value);"   />

按钮的click事件使用js，直接使用js。。。

四、在一些HTML控件的非事件属性中使用（注意：一定要加javascript:）

< a  href ="javascript:void(0);"  onclick ="alert(this.innerText);" > my blog:http://blog.csdn.net/kimsoft </ a >
————————————————
 a标签点击调用js，，使用href=”javascript:xxxxx语法。。。



2、外部JavaScript脚本
外部脚本是使用<script>标签和src属性将外部的JavaScript脚本文件连接到HTML中的方法；这通常用于网页设计领域。

服务端js   ejs框架等

Ref
HTML中调用JavaScript的几种情况和规范写法_KimSoft's Blog-CSDN博客
