Atitit linux 进程保活


  netstat -an | grep ":88886" | awk '{print $0}' | wc -l


#!/bin/sh
tomcat=`netstat -an | grep ":8080" | awk '$1 == "tcp" && $NF == "LISTEN" {print $0}' | wc -l`
 
if [ $tomcat -eq 0 ];then
  #如果端口没有占用的话要怎么怎么样
  /usr/local/apache-tomcat-jenkins/bin/startup.sh
else
  #如果端口被占用的话要怎么怎么样
  echo "运行正常!"

 
原理 判断端口命令列表存在行数，，如果等于0说明没有重新执行

 ps -ef | grep java | grep -v grep | awk '{print $2}' | xargs kill -9

