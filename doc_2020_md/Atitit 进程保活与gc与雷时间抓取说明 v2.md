Atitit 进程保活与gc与雷时间抓取说明

进程检测保活

Shell 脚本端口保活 
Crontab 定时保活 

Gc
Main方法outime时间
Methodrun 配置超时时间
查询执行路径 定时批量kill
定时批量kill  by  ps -ef  ，查询执行路径
定时业务gc   凌晨时段 

雷时间抓取的的保活配置
## match time

*/60 * * * * java -cp  /target/classes:/lib/libjar/guava-23.6-jre.jar:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*:/lib/libjar/*:/a  com.kok.sport.utils.mockdata.WebdriverFirefox  5000

