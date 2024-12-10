hiteck nmspc   命名空间的实现



模块其实就是mmkj

十 jarkas 大鱼 刘洋 汤姆, [17/08/2023 6:10 am]
首先，JavaScript里没有namespace关键字用于声明命名空间。如果在NodeJS有模块的概念，模块其实就是mmkj

十 jarkas 大鱼 刘洋 汤姆, [17/08/2023 6:11 am]
模块化分割函数都有多重方法。mmkj是个方法，，才有node的模块也是个方法，使用file分割也可。。还有pkg模式，，使用前缀模式

十 jarkas 大鱼 刘洋 汤姆, [17/08/2023 6:35 am]
外围的fun使用nmspc模式 
优点 安全 。也方便命名，与人方便查找资料从web 

可读性函数命名。规格可以参考sdk  方便理解和查找资料


提升代码的可读性函数命名。规格可以参考sdk  方便理解和查找资料


#模块&命名空间  文件模块法
TypeScript 在 1.5 版本之前，有内部模块和外部模块的概念，从 1.5 版本开始，内部模块改称作命名空间（下个小节会讲），外部模块改称为模块。

十 jarkas 大鱼 刘洋 汤姆, [17/08/2023 5:21 am]
全局变量名冲突的最好办法还是创建命名空间，下面是在JS中合建命名空间的几种常用方法。


通过函数（function)创建

这是一种比较常见的写法，通过声明一个function实现，函数里设置初始变量，公共方法写入prototype，如：

十 jarkas 大鱼 刘洋 汤姆, [17/08/2023 5:24 am]
吗避免全局变量名冲突的最好办法还是创建命名空间，下面是在JS中合建命名空间的几种常用方法。


通过函数（function)创建

这是一种比较常见的写法，通过声明一个function实现，函数里设置初始变量，公共方法写入prototype，如

十 jarkas 大鱼 刘洋 汤姆, [17/08/2023 5:26 am]
Function的简洁写法

这是一种比较简洁的实现，结构紧凑，通过function实例，且调用时无需实例化（new），方案


使用 global变量，，，xxx\bbb\ccc 路径模式来为key实现
可以分散不同的匿名函数和变量


函数名   前缀法实现，，分割使用双下划线



十 jarkas 大鱼 刘洋 汤姆, [18/08/2023 12:23 am]
可能需要这样来使用   $nmspc/varname

十 jarkas 大鱼 刘洋 汤姆, [18/08/2023 12:29 am]
我们要获取到当前活动符号表可以通过 get_defined_vars 方法来获取。get_defined_vars // 返回所有已定义的变量所组成的数组

根据变量的值查找变量名字，但要注意，有可能有相同值的变量存在。

因此先将当前变量的值保存到一个临时变量中，然后再对原变量赋唯一值，以便查找出变量的名字，找到名字后，将临时变量的值重新赋值到原变量

十 jarkas 大鱼 刘洋 汤姆, [18/08/2023 12:32 am]
使用 NAMESPACE 常量可以输出当前的命名空间，在调试时有用

jark ma, [18/08/2023 12:38 am]
58

不可以。您可以在声明命名空间后设置变量，但变量将始终存在于全局范围内。它们永远不会绑定到名称空间。您可以从缺少任何名称解析描述的情况中推断出这一点

常见问题解答：关于命名空间您需要了解的事情(PHP 5 >= 5.3.0)
也没有允许的语法来在命名空间中定位变量。

jark ma, [18/08/2023 12:39 am]
18

不，正如马里奥所说，他们不能。

要封装变量，请使用Classes。绝对应该避免污染全局变量空间。

jark ma, [18/08/2023 12:43 am]
可能非常糟糕，绝不应该这样做，但是可以通过使用变量变量和命名空间的魔术常数来实现。因此，使用一个字符串变量来命名我们要使用的变量，如下所示：

namespace your\namespace;

$varname = NAMESPACE.'\your_variablename'; //NAMESPACE is a magic constant

$namespaced_variable = $$varname; //Note the double dollar, a variable variable

?>

jark ma, [18/08/2023 12:51 am]
不可能的，因为$MYVARNAME仍然在全局范围内。尝试以下代码。

命名空间.php

<?php
    namespace MYNAME;
    use MYNAME as M;
    const MYVAR   = 'MYVARNAME';

    ${M\MYVAR}    = date('Y');
    echo $MYVARNAME;  // PRINT YEAR
    $MYVARNAME    = 'X';
    echo $MYVARNAME;  // PRINT X
    echo ${M\MYVAR} ; // PRINT X

    include('file.php')

jark ma, [18/08/2023 12:51 am]
您可以通过将变量包装在函数内来将变量绑定到命名空间。

<?php
 namespace furniture;
// instead of declaring a $version global variable, wrap it inside a function
function version(){
 return "1.3.4";
}
?>

jark ma, [18/08/2023 12:55 am]
以使代码更有条理的替代方法：

而不是像 \view\header\$links 那样：

(1) 数组键中的反斜杠用于假想嵌套，示例：

$myVar['view\header\links'] = 'value';

// OR use multidimentional

jark ma, [18/08/2023 1:01 am]
命名空间的另外一种实现方式。就是使用glb数组即可哈哈。绑定到匿名函数

jark ma, [18/08/2023 1:03 am]
秘密空间可以通过函数导来实现，也可以通过变量嵌套来实现。命名空间是space name。

jark ma, [18/08/2023 1:05 am]
）变量名中使用__（双下划线）进行想象嵌套，示例

jark ma, [18/08/2023 1:06 am]
可以使用双下滑线前缀作为mmkj，，也可以有ide推导扒拉哈哈。。函数名



