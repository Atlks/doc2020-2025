Atitit 内容展示算法 整理

防止一成不变

时间倒序，+ 随机排列 +内容抵消


$typeid=(int)($_GET['typeid']);$lmt=(int)($_GET['lmt']);
$sql="SELECT   GROUP_CONCAT(vod_id)   FROM `mac_vod`  WHERE   type_id = $typeid  ORDER BY  vod_time_add  DESC    LIMIT 120";
echo $sql."\n";
$ids=fetchColumnVal($sql);

$sql="select GROUP_CONCAT(vod_id) from ( 
    SELECT     *  from mac_vod where vod_id in ( $ids )  order by rand()  limit $lmt 
    ) t";
echo $sql."\n";
$ids2=fetchColumnVal($sql);
echo 'ids2:'.$ids2."\n";
$sql="
select *,FROM_UNIXTIME(vod_time_add)  from mac_vod where vod_id in ( $ids2 )
order by vod_time_add desc  limit $lmt
";




