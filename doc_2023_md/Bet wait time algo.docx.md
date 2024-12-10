Bet wait time algo


Bet wait time
$bet_time_sec_ramain = $countdown_time_sec - $waring_time_sec;


*/
function getBettimeRemain() {
//  $bet_time = Setting::find(6)->value; //1*60*1000;
//  $bet_time_sec = $bet_time / 1000;
//


 $waring_time = Setting::find(7)->value; //30*1000;
 $waring_time_sec = $waring_time / 1000;


 $countdown_time_sec = $GLOBALS['countdownSeconds'];// if countdown_time_sec120s,so the bettime60s
 //if countdown_time_sec 100s,so bettime 60-(120-countdown_time_sec)

 $bet_time_sec_ramain = $countdown_time_sec - $waring_time_sec;


 $bet_time_sec_ramain_adjust = $bet_time_sec_ramain > 0 ? $bet_time_sec_ramain : 0;

 $bet_time_sec_ramain_adjust = \chkRemainTime_forBet($bet_time_sec_ramain_adjust);


 //  $bet_time_sec = 10;
 var_dump(' $bet_time_sec:' . $bet_time_sec_ramain_adjust);

 return $bet_time_sec_ramain_adjust;
}




Wagnirng waity time

function getWarningBetTimeRemain() {


 //if cnt down not pass,use db delay

 $waring_time = Setting::find(7)->value; //30*1000;
 $waring_time_sec = $waring_time / 1000;


//alread bet some sec,then here warn bet timer
 if ($GLOBALS['countdownSeconds'] >= $waring_time_sec)
   return $waring_time_sec;


 //if cntdown sec too mini ,,,last time watit is 0..so onloy cntdown time is ok
 if ($GLOBALS['countdownSeconds'] < $waring_time_sec) {
   $waring_time_sec_remain = chkRemainTime_forBet($GLOBALS['countdownSeconds']);
   return $waring_time_sec_remain;
 }
 // return $GLOBALS['countdownSeconds'];


}

