Atitt 云视频  自主拼装推流 播放拉流地址url api


配置地址
https://hxcsxs.xsitehub.com//api/cfg.json

{
"push_domain":"155484.livepush.myqcloud.com"
,
"push_domain2":"push.sunboyan.cn"
,
"pull_domain":"pull.sunboyan.cn",
"license_url":"https://license.vod2.myqcloud.com/license/v2/1308109727_1/v_cube.license",
"license_key":"5ada199f8b4660dd48ad8f887dc64127",
"app_secretKey":"aa6440f5eb23a7e5ae772eaa45ebf3930fe50335984511d64a84503f17e6d11d"

}


推流
/api/get_push_addr.php?streamName=stream6

输出类似
rtmp://155484.livepush.myqcloud.com/live/s6?txSecret=cb42752c282fa28e504009d9686805df&txTime=619478E3


拉流 播放url

/api/get_pull_addr.php?streamName=stream6

输出

rtmp://pull.sunboyan.cn/live/stream6?txSecret=0a5cd38a0d6a3c9be8e149ffa6fb516e&txTime=61948F7D

Other
自主拼装推流 URL
自主拼装播放 URL
自主拼装 RTC 连麦/PK URL
前提条件
已注册腾讯云账号，并开通 腾讯云直播服务。
已在 域名注册 申请域名，并备案成功。
已在【云直播控制台】>【域名管理】中添加推流/播放域名，具体操作请参见 添加自有域名。
成功 配置域名 CNAME。

手动生成直播 URL
登录云直播控制台。
选择进入【辅助工具】>【地址生成器】，进入如下配置：
按需选择生成类型。
选择您已添加到域名管理里对应的域名。
按需编辑 AppName。AppName 为区分同一个域名下多个 App 的地址路径，默认为 live。
填写自定义的流名称 StreamName。
选择地址过期时间。
单击【生成地址】即可生成您需要的推流/播放地址。

说明：
AppName 可自定义，仅支持英文字母、数字和符号。
除上述方法，您还可以在云直播控制台的【域名管理】中，选择推流域名单击【管理】，选择【推流配置】，输入推流地址的过期时间和自定义的流名称 StreamName，单击【生成推流地址】即可生成推流地址。

查看推流地址示例代码
进入【云直播控制台】>【域名管理】，选中事先配置的推流域名，【管理】>【推流配置】页面下半部分有【推流地址示例代码】（PHP 和 Java 两个版本）演示如何生成防盗链地址。更多详情操作请参见 推流配置。


自主拼装推流 URL
实际产品中，当直播间较多时，您不可能为每一个主播手工创建推流和播放 URL，您可通过服务器自行拼装推流和播放地址，只要符合腾讯云标准规范的 URL 就可以用来推流，如下是一条标准的推流 URL，它由四个部分组成：


Domain
推流域名，可使用腾讯云直播提供的默认推流域名，也可以用自有已备案且 CNAME 配置成功的推流域名。
AppName
直播的应用名称，默认为 live，可自定义。
StreamName（流 ID）
自定义的流名称，每路直播流的唯一标识符，推荐用随机数字或数字与字母组合。
鉴权 Key（非必需）
包含 txSecret 和 txTime 两部分：txSecret=Md5(key+StreamName+hex(time))&amp;txTime=hex(time)。
开启推流鉴权后需使用包含鉴权 Key 的 URL 进行推流。若未开启推流鉴权，则推流地址中无需 “?” 及其后内容。
txTime（地址有效期）
表示何时该 URL 会过期，格式支持十六进制的 UNIX 时间戳。
说明：
例如5867D600代表2017年1月1日0时0点0分过期，我们的客户一般会将 txTime 设置为当前时间24小时以后过期，过期时间不要太短也不要太长，当主播在直播过程中遭遇网络闪断时会重新恢复推流，如果过期时间太短，主播会因为推流 URL 过期而无法恢复推流。

txSecret（防盗链签名）
用以防止攻击者伪造您的后台生成推流 URL，计算方法参见 最佳实践-防盗链计算。

自主拼装播放 URL
播放地址主要由播放前缀、播放域名（domain）、应用名称（AppName）、流名称（StreamName）、播放协议后缀、鉴权参数以及其他自定义参数组成。例如：
