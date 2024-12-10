Atitit 用户留存功能设计文档整理

一周以后用户留存列表 与统计数量

select user_name,  from_unixtime(user_reg_time),from_unixtime(user_login_time),
from_unixtime(user_last_login_time) from mac_user

则计算最后登录时间》注册时间7天的。。







