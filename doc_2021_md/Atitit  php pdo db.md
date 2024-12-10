Atitit  php pdo db

<?php


$mysql_conf = array(
    'host' => 'pgm-j6c4r878wvy3680zfo.pg.rds.aliyuncs.com',
    'db' => 'postgres',
    'db_user' => 'postgres',
    'db_pwd' => 'woaitav1314!',
    'port'=>1433
);
$dbstr="pgsql:host=" . $mysql_conf['host'] . ";port=". $mysql_conf['port'].";dbname=" . $mysql_conf['db'];
//print_r($dbstr);
$pdo = new PDO($dbstr, $mysql_conf['db_user'], $mysql_conf['db_pwd']); //创建一个pdo对象
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

$pdo->exec("set names 'utf8'");
<?php


//  Workerman version:3.5.25          PHP version:5.6.31

require_once(__DIR__ . '/Workerman/Autoloader.php');  //. 
require_once "conn.php";


use Workerman\Worker;
use Workerman\Lib\Timer;


function task1()
{

    $sql =<<<EOF
            select * from help_topic limit 10;
EOF;

    $glb['sql']=$sql;
//print_r($glb);
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
task1();
die();

