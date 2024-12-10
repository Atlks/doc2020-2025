Tg 机器人文档


机器人如何工作？
有关机器人功能的详细说明，请参阅本指南
Telegram 机器人是不需要电话号码即可设置的特殊帐户。机器人连接到其所有者的服务器，该服务器处理用户的输入和请求。
Telegram 的中间服务器处理所有加密以及与 Telegram API 的通信。开发人员通过简单的 HTTPS 接口与简化版本的Telegram API（称为Bot API）与该服务器进行通信。
机器人与用户有何不同？
机器人能够以用户帐户无法处理的方式处理输入和请求，但机器人和普通用户之间存在一些差异。
机器人没有“上次出现”或在线状态 - 相反，它们在聊天中显示“机器人”标签。
机器人的云存储空间有限——较旧的消息可能会在处理后不久被服务器删除。
机器人无法与用户开始对话。用户必须将他们添加到组中或先向他们发送消息。人们可以搜索您的机器人的用户名或通过其独特的 t.me/bot_username 链接开始聊天。
默认情况下，添加到群组的机器人只能看到聊天中的相关消息（请参阅隐私模式）。
机器人从不吃饭、睡觉或抱怨（除非另有明确编程）。
机器人链接
机器人用户名通常需要“bot”后缀，但有些机器人没有后缀，例如@stickers、@gif、@wiki或@bing。
任何人都可以将可收集的用户名分配给机器人，包括那些没有“bot”后缀的用户名。
如何创建机器人？
创建 Telegram 机器人非常简单，但您至少需要一些计算机编程技能。
Telegram 的 Bot API 简化了机器人的创建过程，它提供了集成代码所需的工具和框架。首先，请在 Telegram 上向@BotFather发送消息以注册您的机器人并接收其身份验证令牌。
您的机器人令牌是其唯一标识符 - 将其存储在安全的地方，并且仅与需要直接访问机器人的人共享。每个拥有您代币的人都可以完全控制您的机器人。





十 jarkas 刘洋 汤姆, [03/06/2022 11:04 am]
/newbot

BotFather, [03/06/2022 11:04 am]
Alright, a new bot. How are we going to call it? Please choose a name for your bot.

十 jarkas 刘洋 汤姆, [03/06/2022 11:04 am]
msg2022bot

BotFather, [03/06/2022 11:04 am]
Good. Now let's choose a username for your bot. It must end in `bot`. Like this, for example: TetrisBot or tetris_bot.

十 jarkas 刘洋 汤姆, [03/06/2022 11:05 am]
msg2022_bot

BotFather, [03/06/2022 11:05 am]
Done! Congratulations on your new bot. You will find it at t.me/msg2022_bot. You can now add a description, about section and profile picture for your bot, see /help for a list of commands. By the way, when you've finished creating your cool bot, ping our Bot Support if you want a better username for it. Just make sure the bot is fully operational before you do this.

Use this token to access the HTTP API:
5464498785:AAGtLv-M-RKgRoIh5G3XEfkdqkCPiVBB1NA
Keep your token secure and store it safely, it can be used by anyone to control your bot.

For a description of the Bot API, see this page: https://core.telegram.org/bots/api




如何使用 PHP 启动 Telegram Bot-慕源网
