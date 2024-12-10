bk  Prgrm scry design Web 安全 


输入安全 防止注入代码
程序运行安全，防止奔溃 ex机制 err机制   try catch  全局钩子ex err钩子
程序运行安全 看门狗  进程守护



什么是 PHP 过滤器？
PHP 过滤器用于验证和过滤来自非安全来源的数据。
测试、验证和过滤用户输入或自定义数据是任何 Web 应用程序的重要组成部分。
PHP 的过滤器扩展的设计目的是使数据过滤更轻松快捷。



您应该始终对外部数据进行过滤！
输入过滤是最重要的应用程序安全课题之一。
什么是外部数据？
来自表单的输入数据
Cookies
Web services data
服务器变量
数据库查询结果



函数和过滤器
如需过滤变量，请使用下面的过滤器函数之一：
filter_var() - 通过一个指定的过滤器来过滤单一的变量
filter_var_array() - 通过相同的或不同的过滤器来过滤多个变量
filter_input - 获取一个输入变量，并对它进行过滤
filter_input_array - 获取多个输入变量，并通过相同的或不同的过滤器对它们进行过滤
在下面的实例中，我们用 filter_var() 函数验证了一个整数：
实例
<?php $int = 123; if(!filter_var($int, FILTER_VALIDATE_INT)) { echo("不是一个合法的整数");



Validating 和 Sanitizing
有两种过滤器：
Validating 过滤器：
用于验证用户输入
严格的格式规则（比如 URL 或 E-Mail 验证）
如果成功则返回预期的类型，如果失败则返回 FALSE
Sanitizing 过滤器：
用于允许或禁止字符串中指定的字符
无数据格式规则
始终返回字符串
验证输入
让我们试着验证来自表单的输入。
我们需要做的第一件事情是确认是否存在我们正在查找的输入数据。
然后我们用 filter_input() 函数过滤输入的数据。
在下面的实例中，输入变量 "email" 被传到 PHP 页面：
实例
<?php if(!filter_has_var(INPUT_GET, "email")) { echo("没有 email 参数"); } else { if (!filter_input(INPUT_GET, "email", FILTER_VALIDATE_EMAIL)) { echo "不是一个合法的 E-Mail";



净化输入
让我们试着清理一下从表单传来的 URL。
首先，我们要确认是否存在我们正在查找的输入数据。
然后，我们用 filter_input() 函数来净化输入数据。
在下面的实例中，输入变量 "url" 被传到 PHP 页面：
<?phpif(!filter_has_var(INPUT_GET, "url")){
    echo("没有 url 参数");}else{
    $url = filter_input(INPUT_GET, 
    "url", FILTER_SANITIZE_URL);
    echo $url;

