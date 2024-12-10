
移动直播SDK 常见问题
https://main.qcloudimg.com › raw › product › pdf

PDF
实际产品中，当直播间较多时，您不可能为每一个主播手工创建推流和播放URL，您可通过服务器自行拼装推流和. 播放地址，只要符合腾讯云标准规范的URL 就可以用来推流， ..



自主拼装推流 URL 实际产品中，当直播间较多时，您不可能为每一个主播手工创建推流和播放 URL，您可通过服务器自行拼装推流和 播放地址，只要符合腾讯云标准规范的 URL 就可以用来推流，如下是一条标准的推流 URL，它由四个部分组成： Domain 推流域名，可使用腾讯云直播提供的默认推流域名，也可以用自有已备案且 CNAME 配置成功的推流域名。 AppName 直播的应用名称，默认为 live，可自定义。 StreamName（流 ID） 自定义的流名称，每路直播流的唯一标识符，推荐用随机数字或数字与字母组合。 鉴权 Key（非必需） 包含 txSecret 和 txTime 两部分： txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)。 开启推流鉴权后需使用包含鉴权 Key 的 URL 进行推流。若未开启推流鉴权，则推流地址中无需 “?” 及其后 内容。 txTime（地址有效期） 表示何时该 URL 会过期，格式支持十六进制的 UNIX 时间戳。 txSecret（防盗链签名） 用以防止攻击者伪造您的后台生成推流 URL，计算方法参见 最佳实践-防盗链计算。 自主拼装播放 URL 说明： 例如 5867D600 代表2017年1月1日0时0点0分过期，我们的客户一般会将 txTime 设置为当前时间 24小时以后过期，过期时间不要太短也不要太长，当主播在直播过程中遭遇网络闪断时会重新恢复推 流，如果过期时间太短，主播会因为推流 URL 过期而无法恢复推流。 移动直播 SDK 版权所有：腾讯云计算（北京）有限责任公司 第8 共57页 播放地址主要由播放前缀、播放域名（domain）、应用名称（AppName）、流名称（StreamName）、播放 协议后缀、鉴权参数以及其他自定义参数组成。例如： webrtc://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&tx Time=hex(time) http://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&t xTime=hex(time) rtmp://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTi me=hex(time) http://domain/AppName/StreamName.m3u8?txSecret=Md5(key+StreamName+hex(time))&am p;txTime=hex(time) 播放前缀 播放协议 播放前缀 备注 WebRTC webrtc:// 强烈推荐，秒开效果最好，支持超高并发。 HTTP-FLV http:// 或 https:// 推荐，秒开效果好，支持超高并发。 RTMP rtmp:// 不推荐，秒开效果差，不支持高并发 HLS（m3u8） http:// 或 https:// 手机端和 Mac safari 浏览器推荐的播放协议。 Domain 播放域名，自有已备案且 CNAME 配置成功的播放域名。 AppName 直播的应用名称，用于区分直播流媒体文件存放路径，默认为 live，可自定义。 StreamName（流名称） 自定义的流名称，每路直播流的唯一标识符，推荐用随机数字或数字与字母组合。 鉴权参数（非必需） 包含 txSecret 和 txTime 两部分： txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)。 开启播放鉴权后需使用包含鉴权 Key 的 URL 进行播放。若未开启播放鉴权，则播放地址中无需 “?” 及其后 内容。 txTime（地址有效期）： 表示何时该 URL 会过期，格式支持十六进制的 UNIX 时间戳。 txSecret（防盗链签名）：用以防止攻击者伪造您的后台生成播放 URL，计算方法参见 最佳实践-防盗链



