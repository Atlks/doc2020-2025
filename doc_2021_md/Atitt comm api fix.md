Atitt comm api fix
格式转换
Xml转换json接口。。
<?php

$xml = simplexml_load_file($_GET['xmlpath']);
echo json_encode($xml);

?>


需要xml有个root才可以

其他一些业务功能

配置修改功能
主要涉及json xml配置文件
