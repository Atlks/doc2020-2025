Atitit mysql event ext 定时调度系统

Mysql event

 insert sys_event set event_def='new com.kok.sport.utils.mockdata.unitRecentlyV2().Live_Match_list_stat_score_today()',event_name='Live_Match_list_stat_score_today'


DROP TABLE IF EXISTS `sys_event`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `sys_event` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `event_name` varchar(45) NOT NULL,
  `event_def` varchar(444) NOT NULL,
  `enable_status` varchar(45) DEFAULT NULL,
  `event_comment` varchar(45) DEFAULT NULL,
  `rzt` varchar(4445) DEFAULT NULL,
  `nextSttScript` varchar(45) DEFAULT NULL,
  `crtime` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `exe_stt` int(11) NOT NULL DEFAULT '0',
  `ext` json DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `unievt` (`event_name`,`event_def`,`exe_stt`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=550 DEFAULT CHARSET=utf8mb4;
/*!40101 SET character_set_client = @saved_cs_client */;


Event ext java
/kok-sport-service/src/main/java/com/kok/sport/utils/db/EventMysqlExt.java

package com.kok.sport.utils.db;

import java.util.LinkedHashMap;
import java.util.List;
import java.util.Timer;
import java.util.TimerTask;

import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.logging.log4j.LogManager;

import com.kok.sport.utils.CaptchData;
import com.kok.sport.utils.ql.MethodRunner;

// T(com.kok.sport.utils.db.EventMysqlExt).main()
public class EventMysqlExt {
	public static SqlSessionFactory sqlSessionFactory1 = MybatisUtil.getSqlSessionFactoryRE();
	static org.apache.logging.log4j.Logger logger = LogManager.getLogger(EventMysqlExt.class);

	public static void main(String[] args) {
		int minisecEvtRecyl = 3000;
//		Timer tmr = new Timer("time2");
//	
//		tmr.schedule(new TimerTask() {
//
//			@Override
//			public void run() {
//
//			
//
//			}
//
//			
//		}, 50, minisecEvtRecyl);
		
		for(int i=0;i<20;i++) {
			try {
				
				String sql = "call exeEvtGet() ";
				logger.info(sql);
				List<LinkedHashMap> es = MybatisUtil.getMybatisMapper(sqlSessionFactory1).querySql(sql);
				for (LinkedHashMap em : es) {

					exeEvent(em);//thread

				}
				Thread.sleep(minisecEvtRecyl);
			} catch (Exception e) {
				logger.error(e);
			}
			System.out.println("getconnStatChkTmr:run");
		}
		System.out.println("f");
	}
	
	public static void exeEvent(LinkedHashMap em) {
		new Thread(new Runnable() {

			@Override
			public void run() {
				try {
					String e_def = (String) em.get("event_def");
					logger.info("==>exeEvent:"+e_def);
					MethodRunner.main(new String[] { e_def });
					String sql = "call exeEvtFns( " + em.get("id")+")";
					logger.info("==>"+sql);
					logger.info(">>>" + MybatisUtil.getMybatisMapper(sqlSessionFactory1).update(sql));
				} catch (Throwable e) {
					logger.error(e);
				}

			}
		}).start();
	}

}

Linux crontab 加入
  * * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "T(com.kok.sport.utils.db.EventMysqlExt).main(null)"


Sp  
exeEvtGet
DELIMITER ;;
CREATE DEFINER=`root`@`%` PROCEDURE `exeEvtGet`()
BEGIN

	#Routine body goes here...

   select * from sys_event where exe_stt =0; 

   update sys_event set exe_stt=1;

END ;;

exeEvtFns


DELIMITER ;;
CREATE DEFINER=`root`@`%` PROCEDURE `exeEvtFns`(`evtid` int)
BEGIN

	#Routine body goes here...



   insert sys_event_log   select * from sys_event where id=evtid;

   delete  from sys_event   where id=evtid;

	update sys_event_log set rzt=now() where id=evtid;

END ;;

