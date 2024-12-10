Tlgrm telegram增加按钮跳转url.docx


Button.json


[

 [
   {
     "text": "验证",
     "url": "https://tronscan.org/#/block/$Blknum"
   }
 ]
]




Xx.php
//add open btn
$buttonTxt = file_get_contents(__DIR__ . "/../../db/button.json");
$buttonTxt=str_replace("\$Blknum",$GLOBALS['Blknum'],$buttonTxt);
$keyboard_array = json_decode($buttonTxt);
$keyboard = new \TelegramBot\Api\Types\Inline\InlineKeyboardMarkup($keyboard_array);


sendMsg($GLOBALS['chat_id'], $text,$keyboard);

function sendMsg(mixed $chat_id, string $text,$rplyMkp=null) {
 try {
   require_once __DIR__."/../../lib/logx.php";
   log_enterMethV2(__METHOD__,func_get_args(), "sendMsgLog");

$bot = new \TelegramBot\Api\BotApi($GLOBALS['BOT_TOKEN']);
$bot->sendmessage($chat_id, $text,null,false,null,null,$rplyMkp);



多行多列按钮


[
 [
   {
     "text": "查看余额",
     "callback_data": "query_balance"
   },
   {
     "text": "最近",
     "callback_data": "query_records"
   }
 ],
   [
   {
     "text": " 官方频道?",
     "url": "https://xxxx"
   }
 ]
]

