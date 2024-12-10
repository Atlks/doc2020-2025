Atitit 数据无缝迁移方法总结


双写模式

操作日志项目采用 Springboot 构建，增加了自定义配置项，如下：

#应用写入mongodb标识
writeflag.mongodb: true
#应用写入elasticsearch标识
writeflag.elasticsearch: true

复制代码

项目改造说明：


第一次上线的时候，先将2个写入标识设置为true，双写MongoDB和ES；


对于读，提供2个不同接口，前端自由的切换；


等数据迁移完，没有差异的时候，重新更改flag的值。

从MongoDB迁移到ES后，我们减少了80%的服务器-InfoQ


图示：应用平衡迁移

