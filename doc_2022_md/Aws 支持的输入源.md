Aws 支持的输入源




Input type – required

RTP
Push your source to fixed endpoints with the real-time transport protocol.

RTMP (push)
Push your source to fixed endpoints with the real-time messaging protocol.

RTMP (pull)
Pull your source from external endpoints with the real-time messaging protocol.

HLS
Pull your source from external endpoints with the HTTP protocol.

MP4
Ingest file content from an MP4 file that is on the public internet

TS
Ingest transport stream content from a TS file from external endpoints specified in the url.

MediaConnect
Ingest streaming content from one or two MediaConnect flows

AWS CDI
Push your uncompressed video over AWS Cloud Digital Interface.

Elemental Link
Ingest streaming content from an AWS Elemental Link device


先建立一个input

Validation Errors
inputs[0].uri
Invalid file extension ".m3u8" for input file uri, must use one of the following file extensions: .mp4,.ts,.m2ts



然后一个channel
