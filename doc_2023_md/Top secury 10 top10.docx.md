Top secury 10 top10



A1、注入漏洞

Sql注入，解决，使用参数编码，直接使用nosql
Html xss注入，使用htmlencode编码过滤
Shell注入
Php code注入
Xx.php?call=fun(123)
白名单模式来，只允许调用指定fun

OTHER
Upload漏洞，限制上传php文件。
文件列表定时对比，防止出现未知知php文件
未知文件举报，这个比url映射路由模式更加简单
配置文件泄露，加密保存即可，或者里面只保存一半的key
Db脱裤泄露，数据库加密
禁用危险函数

A2权限问题

允许将主键更改为其他用户的记录，允许查看或编辑其他人的帐户。

主键id使用uuid即可防范词漏洞，防止级联扫描
一个业务系统一个acc user不要混合一起
定时警报更改密码
A3、加密机制失效
描述 首先是确定传输中和静止数据的保护需求。例如，密码、信用卡号、健康记录、个人信息和商业秘密需要额外保护，主要是如果该数据属于隐私法（例如欧盟的通用数据保护条例 (GDPR)）或法规（例如金融数据保护）例如 PCI 数据安全标准 (PCI DSS)。对于所有此类数据：

 数据脱敏 星号代替
确保加密所有静态敏感数据

A4、安全配置错误
默认帐户及其密码仍处于启用状态且未更改。
错误处理向用户显示堆栈跟踪或其他信息过多的错误消息。
A5、易受攻击或过时组件
自己实现lib

A6、身份验证失败
描述 确认用户的身份、身份验证和会话管理对于防止与身份验证相关的攻击至关重要。如果应用程序存在以下情况，则可能存在身份验证漏洞：
允许自动攻击，例如撞库，其中攻击者拥有有效用户名和密码的列表。
允许蛮力或其他自动攻击
允许使用默认密码、弱密码或众所周知的密码，例如“Password1”或“admin/admin”。

使用弱或无效的凭据恢复和忘记密码流程，例如无法确保安全的“基于知识的答案”。
使用纯文本、加密或弱散列密码（请参阅 A3:2017-敏感数据暴露）。
缺少或无效的多因素身份验证。
在 URL 中公开会话 ID（例如，URL 重写）。
成功登录后不要轮换会话 ID。
·  在可能的情况下，实施多因素身份验证以防止自动凭证填充、暴力破解和被盗凭证重用攻击。
·  不要使用任何默认凭据进行交付或部署，尤其是对于管理员用户。
·  实施弱密码检查，例如针对前 10,000 个最差密码列表测试新密码或更改的密码。
·  将密码长度、复杂性和轮换策略与 NIST 800-63b 的第 5.1.1 节中关于记忆秘密的指南或其他现代的、基于证据的密码策略保持一致。
·  通过对所有结果使用相同的消息，确保注册、凭据恢复和 API 路径能够抵御帐户枚举攻击。
·  限制或增加延迟失败的登录尝试。当检测到凭证填充、暴力破解或其他攻击时，记录所有故障并提醒管理员。

 A8、安全日志记录和监控不足

Insufficent Logging & Monitoring（日志记录和监控不足）

描述 回到 2021 年 OWASP 前 10 名，该类别旨在帮助检测、升级和响应主动违规行为。如果没有日志记录和监控，就无法检测到漏洞。任何时候都会发生日志记录、检测、监控和主动响应不足的情况：
不记录可审计的事件，例如登录、失败登录和高价值交易。
警告和错误不会生成、不充分或不清楚的日志消息。
不会监控应用程序和 API 的日志是否存在可疑活动。
日志仅存储在本地。
适当的警报阈值和响应升级流程没有到位或有效。

如何预防 开发人员应实施以下部分或全部控制措施，具体取决于应用程序的风险：
确保所有登录、访问控制和服务器端输入验证失败都可以用足够的用户上下文来记录，以识别可疑或恶意帐户，并保留足够的时间以允许延迟取证分析。
确保以日志管理解决方案可以轻松使用的格式生成日志。
确保日志数据编码正确，以防止对日志或监控系统的注入或攻击。
确保高价值交易具有带有完整性控制的审计跟踪，以防止篡改或删除，例如仅追加数据库表或类似的。
DevSecOps 团队应该建立有效的监控和警报，以便快速检测和响应可疑活动。
制定或采用事件响应和恢复计划，例如 NIST 800-61r2 或更高版本。

A9、服务器端求伪造（SSRF）
描述 每当 Web 应用程序在未验证用户提供的 URL 的情况下获取远程资源时，就会出现 SSRF 缺陷。它允许攻击者强制应用程序将精心设计的请求发送到意外目的地，即使受到防火墙、VPN 或其他类型的网络 ACL 的保护也是如此。

从应用层：
清理和验证所有客户端提供的输入数据
使用肯定的允许列表强制执行 URL 架构、端口和目标
不要向客户端发送原始响应
禁用 HTTP 重定向
A10、不安全的设计

Ddos攻击，数据扫描器

速率限制 API 和控制器访问，以最大限度地减少自动攻击工具的危害

信息泄露
Db和code可部署在一台机器上 
分开部署没意义，一旦拿走code服务器，就能访问db。。只拿到db权限没问题，因为全部加密了

数据db存储加密 不要只依赖权限

不过，这也意味着只要具备对数据的完整访问权，比如数据库操作员和管理员，就可以解密并获取库中所有数据。这样一来，盗取了凭证的外部黑客和被赋予过多权限的恶意内部人便都会对数据形成威胁了。

字段级加密是数据库加密的重要一步—

如今企业内部风险盛行:黑客入侵内网后,通过盗取数据库账号登陆数据库即可窃取数据,运维环境本身多职位、多人员的数据库访问造成内部数据泄露、删库跑路,这都已超越传统安全手段的能力范围。
、应该全部加密 字段加密http传输等
在不器用https的情况下

主键id使用uuid即可防范词漏洞，防止级联扫描
配置文件 impt fld加密
可以只保留一半，另外一半放在code中，或加密aes

线上人员和dev人分离
这样code和db分开了，防止串联。。Dba无法自行恢复信息。。



企业防止内部数据泄露的方法措施
安装监控系统。
在办公室安装摄像头，或者在电脑上安装监控软件。这样的方式在一定程度上可以约束员工的行为，但是也会引起员工的抵触情绪。
禁用USB接口。
直接给主机上锁，禁用USB接口，这是很多研发型企业会采取的方式，这种方法可以防止开发人员恶意拷贝代码等数据，也可以防止U盘或硬盘的病毒扩散。
3、签署保密协议。员工入职的时候，签署保密协议，尤其是开发人员这样敏感的人员，通过签署保密协议，在一定程度上可以约束员工泄密。
4、使用加密软件
。很多科技研发型企业会选择使用加密软件的方式，可以对文档本身进行保护，研发代码等数据无论以何种方式、何种途径泄露，始终是密文，从而保障企业核心机密不被非法窃取。
5、加水印。以桌面水印的形式在终端计算机桌面上显示，可通过文本、点阵、二维码等不同形式将终端相关信息投射到终端计算机桌面上，防止通过拍照、截屏、打印的方式泄露信息。
6、实施网络隔离
。绝大多数企业采取的第一个步骤是将企业内网与互联网进行隔离，将内部数据“困在”内网，同时也能够有效屏蔽外部网络攻击的风险。较大规模的企业还可能对内部网络实施进一步的隔离，比如划分为办公网、研发网、生产网、测试网等，主要用来屏蔽不同部门、不同业务之间的违规数据交换。通过网络隔离的方式，可以有效防止内部核心代码数据泄露。
控制访问权限。
根据员工的等级和权限，只能访问他们工作所需的数据，这样普通开发人员就接触不到涉密信息了。
以上就是企业防止内部数据泄露、保护数据安全的方法措施。对于传统企业而言，防止内部数据泄露的举措虽然安全，但是部署起来成本太高，花费的时间长，运维也相对来说比较麻烦，一些企业有迫切需求的话就不太试用。那么，有没有哪种方案能够满足内部数据防泄露要求，又能迅速灵活的部署完成呢？


