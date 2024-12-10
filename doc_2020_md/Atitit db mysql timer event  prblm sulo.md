Atitit db mysql timer event  prblm sulo


New create chk enable statu
Bcz cp evt is disable。。。Avoid conflict

每天的8点执行

Every 1 day ，，，at   08:00

Cant run
Maybe event stop open it...
Maybe is disable. Event

*/60 * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*   com.kok.sport.utils.mockdata.SqlCmdExe "set GLOBAL event_scheduler=1"
Cant multi line,use begin end  block

