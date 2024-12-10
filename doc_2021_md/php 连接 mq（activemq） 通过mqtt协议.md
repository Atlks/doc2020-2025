  php 连接 mq（activemq） 通过mqtt协议

  php 连接 mq（activemq） 通过mqtt协议


Activemq支持的长连接协议

 Ws  stomp   mqtt   amqp  openwire

安装jdk8和activemq，启动  >C:\apache-activemq-5.14.4\bin\activemq.bat start
会提示各种协议的开放端口号。。

Php的mqtt库使用phpMQTT
Mqtt.php
<?php
//  C:\wamp\bin\php\php7.1.9\php.exe composer.phar install
echo 111;
echo 222;

require('phpMQTT.php');

$server = 'localhost';     // change if necessary
$port = 1883;                     // change if necessary
$username = '';                   // set your username
$password = '';                   // set your password
$client_id = 'phpMQTT-subscriber'; // make sure this is unique for connecting to sever - you could use uniqid()

$mqtt = new Bluerhinos\phpMQTT($server, $port, $client_id);
if(!$mqtt->connect(true, NULL, $username, $password)) {
    exit(1);
}

$mqtt->debug = true;

$topics['namspace/mytopic'] = array('qos' => 0, 'function' => 'procMsg');
$mqtt->subscribe($topics, 0);

while($mqtt->proc()) {

}

$mqtt->close();

function procMsg($topic, $msg){
        echo 'Msg Recieved: ' . date('r') . "\n";
        echo "Topic: {$topic}\n\n";
        echo "\t$msg\n\n";
}

启动 php.exe   Mqtt.php
此时即可连接上mq，在mq的管理控制台可以看到连接的客户端phpMQTT-subscriber



可以看到客户端开创的topic频道namspace/mytopic'






测试发送从mq控制台




Php mqtt客户端接受到消息

