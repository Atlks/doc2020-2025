Atitit php db mysql api


php与mysql的连接有三种API接口，分别是：PHP的MySQL扩展 、PHP的mysqli扩展 、PHP数据对象(PDO) 。在这三种方法中，“民间”很多是倾向于使用PDO，因为其不担有跨库（可以和各个数据库连接和处理）的优点，更有读写速度快的特点。 PDO不仅能防止了sql注入问题，同时是面向对象的，所以不管操作还是使用都是挺方便的！今天分享下PHP5中使用PDO操作数据库的方法！
1.PDO简介
PDO(PHP Data Object) 是PHP 5 中加入的东西，是PHP 5新加入的一个重大功能，因为在PHP 5以前的php4/php3都是一堆的数据库扩展来跟各个数据库的连接和处理，什么 php_mysql.dll、php_pgsql.dll、php_mssql.dll、php_sqlite.dll等等。 PHP6中也将默认使用PDO的方式连接


 



<?php


$mysql_conf = array(
    'host' => 'localhost',
    'db' => 'mysql',
    'db_user' => 'root',
    'db_pwd' => '',
    'port'=>3306
);
$dbstr="mysql:host=" . $mysql_conf['host'] . ";port=". $mysql_conf['port'].";dbname=" . $mysql_conf['db'];
print_r($dbstr);
$pdo = new PDO($dbstr, $mysql_conf['db_user'], $mysql_conf['db_pwd']); //创建一个pdo对象
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

$pdo->exec("set names 'utf8'");


<?php


//  Workerman version:3.5.25          PHP version:5.6.31

require_once(__DIR__ . '/Workerman/Autoloader.php');  //. 
require_once "conn.php";


use Workerman\Worker;
use Workerman\Lib\Timer;

//echo phpinfo();
//die();
function task1()
{

    $sql =<<<EOF
            select * from help_topic limit 10;
EOF;

    $glb['sql']=$sql;
print_r($glb);
    global  $pdo; //use global var
    $sth = $pdo->query($sql);
    $rows = $sth->fetchAll();
    foreach($rows as $row){
        echo "\r\n";
        echo json_encode ($row);
        echo "\r\n";
        $url='http://localhost/';
        echo $url;
        echo file_get_contents($url);
    }
   echo "\r\n";
   // echo json_encode($rows);
}
//task1();
//die();

//-----------------tier
$task = new Worker();

$task->onWorkerStart = function ($task) {

    // 2.5秒

    $time_interval = 2.5;

    $timer_id = Timer::add($time_interval,

        function () {
          //  require_once('task1.php');
          //  http://localhost/
          //  echo "Timer run\n";
            task1();

        }

    );

};

// 运行所有workers

Worker::runAll();

