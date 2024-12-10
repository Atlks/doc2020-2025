Atitit 微软云直播


用于实时传送视频流的软件还需要以下配置：

一个用于广播事件的相机或设备（例如便携式计算机）。


一种本地软件编码器，可对照相机流进行编码，并通过实时消息传递协议 (RTMP) 将其发送到媒体服务实时传送视频流服务。 有关详细信息，请参阅建议的本地实时编码器。 流必须为 RTMP 或“平滑流式处理” 格式





Azure 媒体服务中的流式处理终结点（来源）
2021/09/29



此页面有帮助吗?
在 Microsoft Azure 媒体服务中，流式处理终结点是一种动态（实时）打包和源服务，可使用一个常见流式处理媒体协议（HLS 或 DASH）直接将实时和按需内

命名约定
流式处理 URL 的主机名格式为：{servicename}-{accountname}-{regionname}.streaming.media.azure.net，其中 servicename = 流式处理终结点名称或实时事件名称。
使用默认的流式处理终结点时，将省略 servicename，因此 URL 为：{accountname}-{regionname}.streaming.azure.net。
限制

