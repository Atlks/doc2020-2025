Atitit 循环中调用函数解决方法

直接调用函数最简单。。

但如果mvc框架比如tp5 可能麻烦些。。

此时可以预先在里面循环，调用，把值写入list再输出裂表。。。

这样前端for 就可以不用动，更加普世。。。


因为tp5 和php都是for，，但php更加通用些啊。。。


global  $pdo;
require __DIR__."/../../../conn.php";

var_dump_ati($pdo);
error_log('$pdo cur is ::');
error_log($pdo);
foreach($res['list'] as $k=>&$v){
    $v['ismake'] = 1;
    if($GLOBALS['config']['view']['website_detail'] >0 && $v['website_time_make'] < $v['website_time']){
        $v['ismake'] = 0;
    }
    $v['website_hits_day']=99;
    $url= $v['website_jumpurl'];
    $sql="  select count(1) from mac_wbst_clk  where dt=date_sub(curdate(), interval 1 day) and url='$url'";
    error_log($sql);
    $v['website_hits_day']=  fetchColumnVal($sql);

}

