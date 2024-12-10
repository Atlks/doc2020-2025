Im bot 聊天机器人 bp 最佳实践


思路一个总体的hdlr   

然后里面串行执行具体的kwd hdlr...如果遇到具体的执行hdlr，就zuzhi冒泡。。。。

Bls hdlr..

$json = json_decode($param, true); // decode the JSON into an associative array
$msg=$json ;
if($json['text']=="余额")
{
    $processed=true;
    $chatId = $msg['chat']['id'];
    require_once "tlgrm.php";
    $reply_txt="rcv..:".$json['text'];
    bot_sendMessage($chatId, $reply_txt, $bot_token);
}






<?php

//C:\phpstudy_pro\Extensions\php\php8.0.2nts\php.exe composer.phar require telegram-bot/api 

//                        TelegramBot
//  C:\phpstudy_pro\Extensions\php\php7.4.3nts\php.exe    C:\w\jbbot\tlgrm.php
$chat_id = -960237539;
$bot_token = "6134198347:AAEdHZUkmYrpm0RHUrzZaKK9d11SiEIhSUk";   //msg 2024  msg2024_bot
$bot_token  = "6510408569:AAHrrbsKgCvklwiFje_TKPF-ABMz0kdxn2c"; // msg2025

require __DIR__ . '/vendor/autoload.php';
$bot = new \TelegramBot\Api\BotApi($bot_token);
//$bot->sendmessage($chat_id, "hahtxt");


$fname = $_SERVER['argv'][1];
$param = urldecode($fname);



try {
    require_once __DIR__ . "/tgHdl_pay.php";
} catch (Throwable $e) {
    var_dump($e);
}
var_dump($processed);
if ($processed) {
    exitx();
    return;
}


try {
    require_once __DIR__ . "/tgHdl_bls.php";
} catch (Throwable $e) {
    var_dump($e);
}
if ($processed) {
    exitx();
    return;
}


try {
    require_once __DIR__ . "/tgHdl_bet.php";
} catch (Throwable $e) {
    var_dump($e);
}
if ($processed) {
    exitx();
    return;
}

try {
    require_once __DIR__ . "./tlgrmHdl_temacyo.php";
} catch (Throwable $e) {
    var_dump($e);
}
if ($processed) {
    exitx();
    return;
}

require_once __DIR__ . "./tgHdl_other.php";

if ($processed) {
    exitx();
    return;
}


var_dump("finish.........stmt");

function exitx()
{
    echo "exit...";
}

$json = json_decode($param, true); // decode the JSON into an associative array


