Atitt amz video 亚马逊直播视频


AWS Elemental MediaLive


Inputs



Create 安全组

0.0.0.0/0


Create input rtmp

Input destinations
The destinations to send the content to.
rtmp://3.129.121.229:1935/app1/ins1
rtmp://3.134.163.72:1935/app2/ins2
Input security group (1)


Create chanel



Add output group
Choose output group type
The type of group determines how outputs are transported or packaged.

HLS
Send live audio, video, and captions to smartphones, tablets, computers, and other AWS Media Services with HTTP Live Streaming (HLS).

Archive
Archive your live audio, video, and captions to Amazon S3.

Microsoft Smooth
Send live audio, video, and captions to an origin server or CDN with Microsoft Smooth Streaming.

UDP
Broadcast live audio, video, and captions with RTP or UDP.

RTMP
Push live audio, video, and captions to an RTMP destination.

Frame capture
Send a series of frame capture files to Amazon S3

MediaPackage
Send live audio, video, and captions to AWS Elemental MediaPackage.

Multiplex
Send live audio, video, and captions to a Multiplex.





AWS 上的直播
此 AWS 解决方案实施有什么作用？
Amazon Web Services (AWS) 提供两种 OTT (OTT) 直播视频流解决方案，以经济高效地向 AWS 云中的全球观众提供媒体内容。这两种解决方案都构建了一个高度可用的架构，可提供可靠的实时观看体验。此页面提供了选择最适合您业务需求的实时视频流解决方案的指南。



en Broadcaster Software (OBS) 将实时 RTMP 流推送到 Media Live，但是，AWS 也支持多种方式. Media Live 将流转换为 HLS 块，然后将其推送到 MediaPackage，后者处理打包并提供端点 url。这是一个基本的实现——它可以根据需要以多种方式轻松配置。如果您需要有关步骤的任何帮助，请发表评论。
