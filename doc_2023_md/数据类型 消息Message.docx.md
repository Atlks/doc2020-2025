数据类型 消息Message


格式化的消息（Message）为单位。进程通过操作系统提供的“发送消息/接收消息”两个原语进行数据交换
消息包括消息头和消息体，其中消息头包括：发送进程 ID、接收进程 ID、消息类型、消息长度等格式化信息
Msgid,From,to,type,len,datetime,text

Tlrgrm msg
{
  "message_id": 22021,
  "from": {
    "id": 879006550,
    "is_bot": false,
    "first_name": "十 jarkas 大鱼 刘洋 汤姆",
    "username": "Xxx0079468"
  },
  "chat": {
    "id": -1001903259578,
    "title": "ssc时时彩测试",
    "type": "supergroup"
  },
  "date": 1692518323,
  "text": "单100"
}

消息传递的两种方式：
直接通信方式：消息直接挂到接收进程的消息缓冲队列上
间接通信方式：消息先发送到中间实体（信箱）中，因此也称“信箱通信方式  email系统就是这样






