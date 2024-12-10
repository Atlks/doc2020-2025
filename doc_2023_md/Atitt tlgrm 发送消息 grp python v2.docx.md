Atitt tlgrm 发送消息 grp python



(1).创建telegram机器人

登录Telegram，并找到@BotFather
创建bot成功，你得到了机器人地址，和对应的访问token，然后变成给机器人发送消息。

这是一个测试用的bot：
token：5049056695:AAFfyxCap2I0SZazC0DJ7WPw5oBz9oZcl7A
username：@test1aJHcqb3iU_bot
可以在浏览器中使用url访问：t.me/test1aJHcqb3iU_bot

必须在bot点击start才能启用机器人。

Get grpid

https://api.telegram.org/bot5178273178:AAE7Ev4HbQa22n9rcrbwZK1_LePgHMXCELI/getUpdates


4- 查找 "chat":{"id":-zzzzzzzzzz，-zzzzzzzzzz 是您的聊天 ID（带有负号）。
5-测试：您可以测试使用 curl 向群组发送消息：
curl -X POST "https://api.telegram.org/botXXX:YYYY/sendMessage" -d "chat_id=-zzzzzzzzzz&text=my sample text"
复制
如果您错过了第 2 步，则您要查找的组将没有更新。此外，如果有多个组，您可以在响应中查找组名（“title”：“ group_name ”）。


https://api.telegram.org/bot5464498785:AAGtLv-M-RKgRoIh5G3XEfkdqkCPiVBB1NA/getUpdates

拿不到grpid 可以getme看下是不是本人的bottoken。。。

C:\w\acapi\dev\src\tlgrm.py

Telegram Bot – 在线获取群聊GroupChat ID 教程 -腾讯云开发者社区-腾讯云




