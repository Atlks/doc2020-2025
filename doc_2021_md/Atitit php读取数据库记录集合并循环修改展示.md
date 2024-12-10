Atitit php读取数据库记录集合并循环修改展示

//------------------------ini db sys
$dbstr = "mysql:host=" . $mysql_conf['host'] . ";port=" . $mysql_conf['port'] . ";dbname=" . $mysql_conf['db'];
error_log('$mysql_conf:'.json_encode($mysql_conf));
  var_dump_ati($dbstr); // for secury only dbg can open
global  $pdo;
$pdo = new PDO($dbstr, $mysql_conf['db_user'], $mysql_conf['db_pwd']); //创建一个pdo对象
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);


$rows = queryPdo($sql, $pdo);
foreach($rows as $k => &$v){
  // echo $k.":".$v."\r\n";   //   0:Array
    $v['vod_pic_urlImg']=mac_url_img( $v['vod_pic']);
    $vodid= $v['vod_id'];
    $v['linkHref']= "/index.php/vod/play/id/$vodid/sid/1/nid/1.html";

 //  global  $rows;
 //   　　$rows[$k] = 1;

}


function queryPdo($sql, $pdo)
{
    global $main;
    var_dump_ati( PHP_EOL . $sql . PHP_EOL );
    global $logfile78a;
    try {
        error_log($sql,3, $logfile78a);
    }catch (Exception $e){}

    //  $main->info($sql);
    global $glb;
    $glb['sql'] = $sql;
    var_dump_ati($glb);
    global $pdo; //use global var
    $stmt = $pdo->query($sql);
    $stmt->setFetchMode(PDO::FETCH_ASSOC);
    $rows = $stmt->fetchAll(PDO::FETCH_ASSOC);

    var_dump_ati( 'qury cnt:' . $stmt->rowCount() . PHP_EOL );
    return $rows;
    // return array($pdo, $rows);
}

/**
 * @param $sql
 * @param $pdo
 * @return mixed
 */
function fetchAll_queryRows($sql, $pdo)
{
    global $main;
    var_dump_ati( PHP_EOL . $sql . PHP_EOL );
    //  $main->info($sql);
    global $glb;
    $glb['sql'] = $sql;
    var_dump_ati($glb);
    global $pdo; //use global var
    $stmt = $pdo->query($sql);
    $stmt->setFetchMode(PDO::FETCH_ASSOC);
    $rows = $stmt->fetchAll(PDO::FETCH_ASSOC);

    var_dump_ati( 'qury cnt:' . $stmt->rowCount() . PHP_EOL );
    return $rows;
    // return array($pdo, $rows);
}

/**query scanl val...tsasyon biaolyeo
 * @param $sql
 * @param $pdo
 * @return mixed
 */
function fetchColumnVal($sql)
{
 //   global $pdo;
    global $main;
    var_dump_ati( PHP_EOL . $sql . PHP_EOL );
    error_log($sql);
    //  $main->info($sql);
    global $glb;
    $glb['sql'] = $sql;
    var_dump_ati($glb);
    global $pdo; //use global var
    $stmt = $pdo->query($sql);
    $stmt->setFetchMode(PDO::FETCH_ASSOC);
    $val = $stmt->fetchColumn();

    error_log('$stmt->fetchColumn()::'.$val);
    return $val;
    // return array($pdo, $rows);
}

