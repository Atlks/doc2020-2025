Aitit aop之道


前言 取代oop的技术 aop
可以大力减少了重复代码，提升了可读性，
简化了结构，将oop转化为aop 管道执行模型串联起来

AOP的产生  软件开发方法的演进
     
   1.2 AOP编程思想 把系统看做一批关注点

AOP就是为了解决类似问题，把这些代码与核心逻辑代码剥离，其实现方式就是在现有的类或方法的基础上通过“注解”（Java）、"特性"（C#）、“装饰器”（Python）把核心逻辑代码用各个“方面”的代码包裹起来。（我的理解AOP就是语言层级实现的装饰器模式）

         
第2章 AOP基础理论 核心技术 开源框架

              

常见切面 -表单提交检查 日志 ex auth 异常 Finaly 释放资源  最终增强

http重试  权限等  参数过滤  事务 性能检测
.3.1 增强类型  前置增强   环绕增强  异常抛出增强 
植入切面技术   动态拦截 vs 静态植入
 


7.4.3 静态普通方法名匹配切面 246
7.4.4 静态正则表达式方法匹配

常见实施模式 与核心技术
  动态代理植入 和静态植入
基于注解的植入   （meta元编程）
反射编程，，
管道编程， fp编程 植入 函数组合思想

Eval模式来执行aop
Aop表达式  pipe( chk1,chk2, coreFun)
环绕式式aop 常用在log记录函数进入参数和返回值记录
Pip(chk,  logAop(coreFun) )
也可以普通的前后增强模式组合  pipe( chk1,logFunprm,Fun,logFunRet)
魔术方法_call等   meth missing特性
各种拦截器  触发器技术 Db trigger模式

常见类库与范例
Dsl 管道组合表达式 pipe( chkUname,cashin)  ;


function pipe() {
   let fns = arguments;
   let rzt;

   for (var i = 0; i < fns.length; i++) {
       let f = fns[i];
       rzt = f(rzt);

   }
   // for (f of fns) {
   //
   // }
   return rzt;
}
function  chkSxfUname()
{
   if ($("#uname_sxf").val() == "") {
       throw ("玩家账户不能为空")
   }
}


Php  call_user_fun   vs  js   fun.apply
Eval 函数
 Lodash.flow
 SpEL 316

 Ref
Hitek 提升稳定性  aop技术

Hitek aop编程的最佳实践  php node 
显示部分信息
 Aitit aop之道.docx


《开发者突击：精通AOP整合应用开发：AspectWerk_Java知识分享网-免费Java资源下载.mhtml
