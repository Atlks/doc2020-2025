Atitt tlgrm 发送消息 grp  收发消息 v2 x70 php nodejs pyx 



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

Code
Nodejs 
rcvMsg.js  C:\w\jbbot\rcvMsg.js
//c: \w\ jbbot > C: \phpstudy_pro\ Extensions\ php\ php7 .3 .4 nts\ php.exe think swoole //ink swoole//// 
////////   npm install node-telegram-bot-api

const TelegramBot = require('node-telegram-bot-api');

// replace the value below with the Telegram token you receive from @BotFather
const token = '5464498785:AAGtLv-M-RKgRoIh5G3XEfkdqkCPiVBB1NA';

// Create a bot that uses 'polling' to fetch new updates
const bot = new TelegramBot(token, { polling: true });


// Listen for any kind of message. There are different kinds of
// messages.
bot.on('message', (msg) => {
    const chatId = msg.chat.id;
    console.log(msg);
    // send a message to the chat acknowledging receipt of their message
    bot.sendMessage(chatId, 'Received your message');
});

Php  必须使用webhook接受消息
sleep(3);
//  //  C:\phpstudy_pro\Extensions\php\php7.4.3nts\php.exe    C:\w\jbbot\async.php
$chat_id=-960237539;
$bot_token="5464498785:AAGtLv-M-xxx";

require __DIR__ . '/vendor/autoload.php';
$bot = new \TelegramBot\Api\BotApi($bot_token);
//$bot->sendmessage($chat_id, "hahtxt");

$txt= "task1 msg,slp5";
$url_tmp="https://api.telegram.org/bot$bot_token/sendMessage?chat_id=$chat_id&text=$txt";
echo $url_tmp;

echo file_get_contents($url_tmp);

ref

C:\w\acapi\dev\src\tlgrm.py

Telegram Bot – 在线获取群聊GroupChat ID 教程 -腾讯云开发者社区-腾讯云




