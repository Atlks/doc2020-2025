Atitit 定时任务


比赛状态抓取

# state realtime
* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().jinxinzhon_Football_Live_Match_list_statue()"


定时通知wss接口
 ## TonzhiJinxinzhongList
* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunnerSec "T(com.kok.sport.utils.mockdata.TonzhiJinxinzhongList).main(null)" 7

D:\prj\sport-service\kok-sport-service\target\classes\com\kok\sport\integration\impl\SyncFootballLiveMatchdetailliveImp.class
/target/classes/com/kok/sport/integration/impl/
* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunnerSec "T(com.kok.sport.utils.mockdata.TonzhiJinxinzhongList).main(null)" 3


定时比分拉取
* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunnerSec "new com.kok.sport.utils.mockdata.unitRecentlyV2().Jinxinzhon_Score_tliveRealytimeFootballMatchController_Live_Match_detail_live()" 3

* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunnerSec "new com.kok.sport.utils.mockdata.unitRecentlyV2().jinxinzhon_Football_Live_Match_list_refreshScore()" 3

比赛时间数据抓取
##tiemr ff 实例6：每晚的21:30重启smb
0 14 * * * java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox
0 13 * * * java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox
0 15 * * * java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox
0 16 * * * java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox
0 17 * * * java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox


 
 比赛状态刷新

* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().test__Football_matchStatScoreFlush()"


 */20 * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().test__Football_score_today()"
 
 
 */5 * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().test__Football_teamFlush()"

盘口数据抓取

 */5 * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().jinxinzhong_odds_fresh()"

other
 
  * * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().test__Football_lostMatchFlush()"



  * * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "T(com.kok.sport.utils.db.EventMysqlExt).main(null)"
 
 # socre realtime api
* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().matchStatScoreFlush_LiveMatch_live()"

# tlive realtime  Football.Live.Match_detail_live
* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().tliveRealytimeFootballMatchController()"

进球通知数据拉取

#tlive jincyo tonji  tonji_Live_Match_detail_live
* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunnerSec "new com.kok.sport.utils.mockdata.unitRecentlyV2().tonji_Live_Match_detail_live()" 9


* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*   com.kok.sport.utils.mockdata.TonzhiJinxinzhongList


 拉取球队排名
  
*/3 * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*   com.kok.sport.utils.mockdata.TeamRankFlush
/target/classes/com/kok/sport/utils/mockdata/


other

  
*/60 * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*   com.kok.sport.utils.mockdata.SqlCmdExe "set GLOBAL event_scheduler=1"


yum install links  
lynx  https://live.leisu.com/

*/6 * * * *  java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox 
  
  
  
 nohup  java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox    > WebdriverFirefox.log 2>&1 &
   
  */8 * * * *   nohup  java -cp /data/deployer2/sport-service/kok-sport-service/target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/* com.kok.SportApplication  > SportApplication.log 2>&1 &
  
  
*/70 * * * * ps -ef | grep java | grep -v grep | awk '{print $2}' | xargs kill -9

*/72 * * * * ps ax|grep firefox  | grep -v grep | awk '{print $1}' | xargs kill -9 | java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox 
 
