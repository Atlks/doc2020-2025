Atitit redis js api sdk 接口说明

调用范例
http://localhost/api_redis?param=-cfg g:/redis_11.txt  -get access_token
http://localhost/api_redis?param=-host 101.132.148.11 -port 63790 -pwd ttredis$2018*124 -db 1  -get access_token


参数说明  param ：： url参数 ，，内容时传递给redis处理程序的参数
配置文件模式
http://localhost/api_redis?param=-cfg g:/redis_11.txt  -get access_token

	  
直接指定主机模式
http://localhost/api_redis?param=-host 101.132.148.11 -port 63790 -pwd ttredis$2018*124 -db 1  -get access_token

-host 101.132.148.11 -port 63790 -pwd ttredis$2018*124 -db 1    -get access_token


传递给redis处理程序的参数说明

-host 101.132.148.11 -port 63790 -pwd ttredis$2018*124   -db 1
见到名字知道意思，redis主机端口密码，数据库序号从1开始，为了方便

-get access_token 获取key为access_token的内容，string数据类型，get指令与redis指令一致
 -smembers 300348232050020352_2019_04_02  ，，smembers 指令，获取key为300348232050020352_2019_04_02的内容，set数据类型

支持的redis指令   -get   -smembers 等，详见redis文档

其他redis指令支持
redis-cli -h 101.132.148.11 -p 63790 -a ttredis$2018*124 get   access_token

