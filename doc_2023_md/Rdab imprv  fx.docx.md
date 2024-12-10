Rdab imprv  fx


减少语法噪音


动态语言》》 静态语言

Js php 这类语法噪音小，，java语法噪音太大了。。 可读性动态语言更高

中缀表达式
只有一个参数的情况下，前缀表达式可读性也不错
Good naming
动词命名  动词前缀
强调算法而不是oo
Reg.js        文件命名要和功能命名一致，最简单化动词，不要名词前后缀，复杂的化，加上后缀

Reg()
{


}

Login.js

Login()
{
Chk uname n pwd
saveToken()

}




提升结构可读性
顺序额结构，使用pipe连接  aop模式
If结构，可以fp

function 登录(用户名, 密码) {

   检查用户名密码(用户名, 密码);
   如果(__检查通过,
       那么(() => {
           保存TOKEN()
           显示退出按钮区域()
           关闭登录区域()
           转到主界面();

       }), 否则(() => {
           提示("用户名密码不对")
           终止流程()

       }))

}



Table map表映射模式

使用fp模式提升case foreach结构可读性

提升文件 fun布局部署可读性

Gui fun ，url对应的功能直接映射到文件
Login（） 》》 login。Js

减少了路由多余的东西
Coc 约定大于配置
