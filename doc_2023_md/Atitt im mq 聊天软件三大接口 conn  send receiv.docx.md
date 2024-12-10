Atitt im mq 聊天软件三大接口 conn  send receiv 收发消息

场景的im tlgrm mq




bot = getTelegramBot(token);

bot.on('message', (msg) => {

    //   $msgx = msg.text;
    console.log(msg);
    bot.sendMessage(msg.chat.id, 'Received your message');

    $fname = Math.random();
    writeFileSyncx($fname, JSON.stringify(msg));
    execSyncx($phpexe + " " + $tlghr_msg_hdl + " " + $fname);
    console.log(999)
});


