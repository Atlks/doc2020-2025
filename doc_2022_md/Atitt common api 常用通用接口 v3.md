Atitt common api 常用通用接口

http接口的输入大部分为get模式，也兼容post
大部分为get接口，数据编码模式为默认的application/x-www-form-urlencoded
只有少部分上传文件类用的http post二级制数据模式编码multipart/form-data
数据返回码
数据返回码即是http码，，200代表ok，5xxx代表错误
200 即是ok

但是纯数字返回码可读性较差，所以很多接口也附加业务字符串返回码。。比如ok，，err：xxxx一类的

原始返回数据包括调试信息和业务数据，中间用-----------attilax---分割符分割。。之前是调试信息，方便测试期间调试。。后面是具体的业务数据，一般查询数据类的返回是一个json列表，也有少部分接口返回html和csv数据和纯文本。
修改数据类的接口一般返回文字状态码ok一类的。。

Adfkdasfkljdkajfal  -----------------attilax--- ok


数据库类api 查询接口
Sql执行接口。。
Sq执行接口


Io文件类读写api
文件上传，读写，查看
文件expolore组件很多
内存变量读写web 类型
Coookie session类读写接口

Mq redis接口


Cpu使用task管理。。。
New uplod task。。。
执行task shell
Script run





Other
Cmd接口转rest接口
Im推送类接口

设备管理类接口

格式转换
Xml转换json接口。。
<?php

$xml = simplexml_load_file($_GET['xmlpath']);
echo json_encode($xml);

?>


需要xml有个root才可以


Ref
Os 接口 ，web接口
Atitit 架构简化 与扩展性 常见的通用接口.docx
