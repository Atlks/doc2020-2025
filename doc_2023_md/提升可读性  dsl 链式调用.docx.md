提升可读性  dsl 链式调用 +表映射 + for展开链式



内部dsl
Ai辅助 poliot  自然语言dsl


顺序结构链式调用
Oo模式太麻烦。。实现￥this。.erq lambda繁琐。。

 call_user_func_array   函数值传递可以使用glb


//  chainInvk(array("f1", array(11, 22), "f2", 333, "f3"));


// call_user_func_array()

function chainInvk($prms)
{
   foreach ($prms as $k => $f) :
       if (is_array($f))
           continue;

       if (!function_exists($f)) {
           continue;
       }


       //execFun($f,$prms,$k);
       $fun_prm = getPrm($prms, $k + 1);

       // $f($fun_prm);

       if (!is_array($fun_prm))
           $fun_prm = array($fun_prm);
       call_user_func_array($f, $fun_prm);


   endforeach;


}




Case结构，三元运算符，四元。
。Select结构。。
太空船操作符
以及表映射模式  
自动化映射模式 keywd


Forecah结构  for(stm1,stm2,stm3)展开

