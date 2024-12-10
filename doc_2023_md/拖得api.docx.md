拖得api


封盘结束时接入拖的展示数据

//获取随机拖数据并融合为arr
$records_db = \app\common\Logs::getBetRecordByLotteryNoGrpbyU($lottery_no);
$rows=rdmRcds_ssc(5);
$GLOBALS['$rowsTo']=$rows;
$records= arr_merg_ssc($rows,$records_db);

$text = "--------本期下注玩家---------" . "\r\n";



C:\0prj\sscbot\libBiz\fenpan_toLib.php
rdmRcds_ssc(）
arr_merg_ssc($rows,$records_db)


兑奖时候，接入拖得兑奖结果数据

C:\0prj\sscbot\libBiz\duijiang_tor.php
/**  添加拖列表到正式的列表
 * @param $a  正式列表
 * @return void
 */
function addToList_toDuijEchoList($a)

