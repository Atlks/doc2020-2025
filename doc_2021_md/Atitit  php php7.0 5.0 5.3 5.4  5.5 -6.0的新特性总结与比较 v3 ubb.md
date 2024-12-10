
Atitit  php php7.0 5.0 5.3 5.4  5.5 -6.0的新特性总结与比较
 
paip.php 5.0 5.3 5.4  5.5 -6.0的新特性总结与比较

1. Php8	2
1.1. Jit	2
2. PHP 7 的五大新特性	2
2.1. 组使用声明 	2
3. PHP5的新特性	3
3.1. · 对象的参照过渡是默认的（default）	4
3.2. · 引入访问属性的限制	4
3.3. · 引入访问方法的限制	4
3.4. · 抽象类和抽象方法	4
3.5. · 接口	4
3.6. · final声明	4
3.7. · 名空间	4
3.8. · 类内常量	4
3.9. · 类变量	4
3.10. · 统一构建器	4
3.11. · 析构函数（Distructor）	4
3.12. · 其他附属特性	4
3.12.1. 4、延迟静态绑定	5
3.12.2. ?:  操作符	5
3.12.3. 增强的ini文件支持  INI Magic	5
8. 扩展的 OpenSSL 函数 	5
增强的error handling	6
3.12.4. (1)名字空间,用来解决命名被污染	7
3.12.5. (2)新的魔法函数 __callStatic 原来 __call的静态模式	7
3.12.6. (3)支持变量调用静态，可以通过$someClass::$method()调用	7
3.12.7. (4)新增日期函数date_create_from_format	7
3.12.8. (5)新增了类似JavaScript中的匿名函数和闭包	7
1. (6)新魔法常量 __DIR__ 来解决路径问题	7
3.12.9. 循环垃圾收集	7
3.12.10. SPL 添加了新的内容，包括双重链接表、栈、堆和队列的实现，	8
 getopt() 优化	9
XSLT Profiling 	10
4. ##5.4主要包括以下特性:	10
4.1. ###1. traits (多继承s解决方案)	10
4.2. Array dereferencing support  数组元素赋值到个变量	10
4.3. Short array syntax []	10
4.4. 3.DTrace support	10
4.5. 	10
4.6. 4.Webserver SAPI   /// Buid-in web server	11
4.7. 5. Upload progress	12
4.8. 6. JsonSerializable Interface	12
4.9. 7. Use mysqlnd by default	12
4.10. 高精度计时器	12
5. ##5.5新特性	13
5.1. 1 生成器 yield关键字	13
5.2. 2 finally关键字	13
5.3. 3 foreach 支持list()	13
5.4. 4 empty() 支持自定义函数了	13
5.5. 5 非变量array和string也能支持下标获取了	13
5.6. 6 类名通过::class可以获取	13
5.7. 7 增加了opcache扩展	13
6. ##PHP 6 新特性	14
6.1. Unicode支援	14
6.2. Web 2.0 特性 SOAP	14
 XML增强	14
7. 参考	15

Php8
Jit
PHP 7 的五大新特性
PHP 7 的五大新特性 - 51CTO.COM.mhtml
PHP 7.1 新特性一览-PHPChina开发者社区-权威的PHP中文社区.mhtml

开发进展
编辑
 组使用声明


1

2

3

4

5

6

7

// 显式使用语法:

use FooLibrary\Bar\Baz\ClassA;

use FooLibrary\Bar\Baz\ClassB;

use FooLibrary\Bar\Baz\ClassC;

use FooLibrary\Bar\Baz\ClassD as Fizbo;

// 分组使用语法:

use FooLibrary\Bar\Baz\{ ClassA, ClassB, ClassC, ClassD as Fizbo };2.  

PHP5的新特性 

接下来请按照顺序看一下被强化的PHP5的性能。首先是最为重要的面向对象性能，类的实体特性在大幅度的被修改着。这里说的仅是关于类的新特性。 

· 对象的参照过渡是默认的（default） 
· 引入访问属性的限制 
· 引入访问方法的限制 
· 抽象类和抽象方法 
· 接口 
· final声明 
· 名空间 
· 类内常量 
· 类变量 
· 统一构建器 
· 析构函数（Distructor） 
· 其他附属特性 

作者 老哇的爪子 Attilax ail，  EMAIL:1466519819@qq.com
转载请注明来源： http://blog.csdn.net/attilax

##PHP5.3的新特性你会有个全新的理解和感悟。
　　1、首先对之前滥用的语法进行了规范
　　众所周知PHP在语言开发过程中有一个很好的容错性，导致在数组或全局变量中包含字符串不使用引号是可以不报错的，
2、MySQL驱动Mysqli 提高效率
　　3、PHP5.3安全和性能的提升
　　如md5()大概提高了10%-15%的性能，更好的内存处理机制，提高软件性能的访问。解决了include(require)_once重复打开的问题，之前once都是用静态变量实现的，用gcc4编译的二进制文件将更小，整体性能提高了5%-15%
　　4、延迟静态绑定
PHP的静态是在预编译时就固定好的，所以在继承的时候，父类里的self指的是父类，而不是子类。而php5.3加入了新的语法static，可以在运行时候捕捉当前类

?:  操作符 

增强的ini文件支持  INI Magic

CGI/ FastCGI支持类似.htaccess的INI配置
每个目录下都可以有INI设置，ini的文件名取决于php.ini的配置，但是[PATH=/var/www/domain.com], [HOST=www.domain.com]段落的设置用户不能修改。

* CGI/FastCGI 支持".htaccess" 形式的INI控制
* 用户可以自己设定每个目录的INI在php.ini中通过[PATH=/var/www/domain.com]设定
* 优化错误处理
* 允许用户使用INI变量和常量任何定义的INI文件中
* 其他几个小的优化


用户自定义的php.ini(.htaccess) 文件名. 默认为".user.ini"
user_ini.filename = ".user.ini"

8. 扩展的 OpenSSL 函数

* 使用 OpenSSL Digest 函数

foreach (openssl_get_md_methods() as $d) {// MD4, MD5, SHA512... (12 all in all)
echo $d. " - ". openssl_digest("foo", "md5"); // acbd18db4cc2f85cedef654fccc4a4d8
}
增强的error handling

允许在ini文件中定义变量和常量，可以在程序中直接调用。
附上一段ini文件的例子

　　5、更多新特性
　　(1)名字空间,用来解决命名被污染
　　(2)新的魔法函数 __callStatic 原来 __call的静态模式
　　(3)支持变量调用静态，可以通过$someClass::$method()调用
　　(4)新增日期函数date_create_from_format
　　(5)新增了类似JavaScript中的匿名函数和闭包
(6)新魔法常量 __DIR__ 来解决路径问题
循环垃圾收集
垃圾收集是 PHP 开发人员在性能方面遇到的一个问题。PHP 有一个非常简单的垃圾收集器，它实际上将对不再位于内存范围（scope）中的对象进行垃圾收集。垃圾收集的内部方式是使用一个引用计数器，因此当计数器达到 0 时（意味着对该对象的引用都不可用），对象将被当作垃圾收集并从内存中删除。
这种方式工作得很好，但是如果一个对象使用父子关系引用另一个对象，那就会引发问题。在这种情况下，这些对象的引用计数器没有被收集，因此这些对象使用的内存仍然属于未引用的内存，并且直到完成请求后才能够进行分配。下面看一下关于这种问题的例子。

在 PHP V5.3 中，垃圾收集器将检测这些循环引用，并且能够释放它们所占用的内存，因此在执行脚本时 PHP 内存使用情况将保持平稳。当 Parent 类的每个引用被删除后，Parent 类中的 Child 类引用也将会被当作垃圾收集

 SPL 添加了新的内容，包括双重链接表、栈、堆和队列的实现，
标准 PHP 库（Standard PHP Library，SPL）是 PHP V5 中新增的接口和类的集合，旨在解决标准问题。这些问题包括实现可迭代的对象，使对象具有数组的行为或实现一个链接的列表。这些类和方法的优点是它们是原生的 PHP，这意味用 PHP 本身实现它们会获得更快的速度。在很多情况下，这些类和方法还允许内部 PHP 函数直接使用这些对象，就像 Iterator 接口允许您使用 foreach 结构迭代对象一样。
PHP V5.3 向 SPL 添加了更多的类。我们前面提到一个类就是在 SPL 类 SplDoublyLinkedList 中实现的双重链接列表。它供其他两个新 SPL 类使用：SplStack（实现一个栈）和 SplQueue（实现一个队列）。

* 优化嵌套的目录迭代次数由文件系统迭代

* 引入 GlobIterator

* 各种各样的数据结构类: 双链表, 堆栈, 队列, 堆, 小型堆, 大型堆, 优先级队列


* 其他的很绕口的一些特征
让我们看一看如何使用 SplStack 类实现一个栈。

使您获得了一些常见的数据结构并且可以轻松使用它们。

清单 11. PHP V5.2 及之前版本不能恰当地对父子类关系进行垃圾收集 

 getopt() 优化
getopt() 优化

* 影响 Windows 平台

* 本地的执行不依赖于本地getopt()实现.

* 跨平台支持长选项 (--option)
// input: --a=foo --b --c
var_dump(getopt("", array("a:","b::","c")));
/* output: array(3) {
["a"]=>
string(3) "foo"
["b"]=>
bool(false)
["c"]=>
bool(false)
} */
XSLT Profiling
* 引入 Xslt Profiling 通过 setProfiling()实现

* 影响 Windows 平台

* 本地的执行不依赖于本地getopt()实现.

##5.4主要包括以下特性:
###1. traits (多继承s解决方案)
Array dereferencing support  数组元素赋值到个变量
Short array syntax []
3.DTrace support

php5.4新功能Traits介绍

1. traits (多继承s解决方案)
Traits是在5.4中新增的一个用于实现代码重用的方法。

php是一种单一继承的语言，我们无法像java一样在一个class中extends多个基类来实现代码重用，现在Traits能解决这一代码重用的问题，它能让开发者在多个不同的class中实现代码重用。
Traits和class在语义的定义上都是为了减少代码的复杂性，避免多重继承的问题。

Traits 和class相似，但是仅用于以统一和较细粒度的方式来提供一组功能，在Traits内部无法进行实例化，即不存在类似class的构造函数__construct()。Traits作为一个php传统继承的扩展并实现水平集成;因此，在应用程序的class中可以不再需要继承。

Traits提供了一种灵活的代码重用机制，即不像interface一样只能定义方法但不能实现，又不能像class一样
Traits (横向重用/多重继承)是一组结构很像“类”(但不能实例化)的方法，它可以让开发人员在不同的类中轻松地重用方法。 PHP为单继承语言，子类只能继承一个父类，于是Traits来了。

Traits的最佳应用是多类之间可以共享相同的函数

2.Array dereferencing support  数组元素赋值到个变量
echo myfunc()[1];
3.DTrace support

DTrace是一个性能分析工具, 可以跟踪出函数调用点,返回点等数据, 对于这个我也不是很了解, 感兴趣的同学可以参看PHP 5.3.99-DEV AND DTRACE PART I
4.Webserver SAPI   /// Buid-in web server

最后, PHP5.4还新增了一个SAPI, 这个SAPI将支持直接把PHP当做Websever使用:
 
PHP5.4内置了一个简单的Web服务器，这样在做一些简单程序就方便多了，省去了环境配置的工作，特别对于初学者来说

3. Short array syntax
PHP5.4提供了数组简短语法：

1
$arr = [1,'james', 'james@fwso.cn'];


$fruits = array('apples', 'oranges', 'bananas'); // "old" way

// 学Javascript的数组了

$fruits = ['apples', 'oranges', 'bananas'];

// 关联数组Map in java

$array = [

'foo' => 'bar',

'bar' => 'foo'

];

5. Upload progress
Session提供了上传进度支持，通过$_SESSION["upload_progress_name"]就可以获得当前文件上传的进度信息，结合Ajax就能很容易实现上传进度条了。

参考：http://www.laruence.com/2011/10/10/2217.html

6. JsonSerializable Interface
实现了JsonSerializable接口的类的实例在json_encode序列化的之前会调用jsonSerialize方法，而不是直接序列化对象的属性。
参考：http://www.laruence.com/2011/10/10/2204.html

7. Use mysqlnd by default
现在mysql, mysqli, pdo_mysql默认使用mysqlnd本地库，在PHP5.4以前需要:

高精度计时器

此次引入了$_SERVER['REQUEST_TIME_FLOAT']数组变量，微秒级精度(百万分之一秒，float类型)。对于统计脚本运行时间会非常有用：


##5.5新特性
1 生成器 yield关键字
yield的中文文档在这里：http://php.net/manual/zh/language.generators.overview.php
查看文档，能知道yield的一个功能就是能有效的降低迭代的内存开销。比如官网的这个xrange例子：
2 finally关键字
这个和java中的finally一样，经典的try ... catch ... finally 三段式异常处理。
3 foreach 支持list()
4 empty() 支持自定义函数了
之前empty()中的参数是不能为函数的。现在可以了
5 非变量array和string也能支持下标获取了
6 类名通过::class可以获取
7 增加了opcache扩展
使用opcache会提高php的性能，你可以和其他扩展一样静态编译（--enable-opcache）或者动态扩展（zend_extension）加入这个优化项。




##PHP 6 新特性

PHP 6目前已經作為開發者快照使用，所以你可以下載和試用一下這篇文章列出很多特性，這些特性已經在目前的快照中實現了。見資源。

 Unicode支援

在PHP的核心函數中，有很多對Unicode字串的支援的改進，這些新特性將產生大幅度的影響因為它允許PHP為國際字元提供更多的支援。所以如果一個開發者或者架構師使用不同的語言，例如Java程式語言，是因為它具有超過PHP的國際化支援的話，當支援改進時他會花一點時間來考慮一下PHP。

因為今天你已經可以下載到開發者
Web 2.0 特性 SOAP

依賴於你怎麼使用PHP和你現在Script的是什麼樣子的，現在的語言和語法差異，可能會或者不會最大程度的影響下面一些特性，這是指那些直接讓你引用的Web 2.0功能到你的PHP應用程式。

SOAP
SOAP是一種網路服務「說 話」的協議，並且支援不少其他語言，例如Java和微軟的.NET,雖然有其他的方法來驅動和使用網路服務，比如 表象化狀態轉變（Representational State Transfer ）REST，SOAP仍然在使不同平台具有可操作性中是最常用的。此外，SOAP在PHP擴充和PEAR庫中使用，SOAP在PHP中預設是不支援的，因 此你啟用這個擴充或者叫你的ISP啟用。此外，PEAR包允許你建立SOAP客戶端和伺服器，如SOAP包。

如果你改變了預設設定，SOAP將會在PHP 6中啟用。這個擴充將提供你很容易的的實現SOAP客戶端和SOAP服務，允許你編寫的應用提供使用或者網路服務。

如果SOAP擴充是預設設定，那就意味著你不能在PHP中設定它們，如果您開發的PHP應用程式並且它們發佈到一個ISP伺服器上，您可能需要檢查一下你的ISP，以驗證SOAP並啟用為他們升級。

XML增强 

在PHP 5.1中XMLReader 和XMLWriter已經變成PHP核心的一部分，這使你工作起來更輕鬆如果在你的PHP程式中需要使用到XML的話。和SOAP擴充一樣，如果你使用SOAP或者XML這是個好消息因為PHP 6比已經出爐的PHP4 更適合你。
参考
PHP5.0新特性_PHP_中国网管联盟bitsCN.com.htm
PHP5.3之后的新特性_PHP教程_编程技术.htm
PHP5.3新特性介绍.htm
PHP V5.3 中的新特性，第 1 部分  对象接口的变化.htm
PHP 5.3 5.4新特性整理 – 【人人分享-人人网】.htm

traits：Traits技术初探 - 大CC - 博客园.htm
PHP5.4的新特性   风雪之隅.htm
PHP5.4新特性   喵了个咪.htm
PHP5.4发布：新特性与改动_PHP资讯_精品学习网.htm
PHP 5.5 新特性 - 轩脉刃 - 博客园.htm
PHP 6 的新特性 - 討論PHP的  - 博客园.htm
