Prgrm secury  




代码注入问题


会话（Session）安全
保持 HTTP 会话管理的安全是重要的。会话安全相关内容描述章节在Session 模块 文档下的会话安全部分。
文件系统安全

PHP 被设计为以用户级别来访问文件系统，所以完全有可能通过编写一段 PHP 代码来读取系统文件如 /etc/passwd，更改网络连接以及发送大量打印任务等等。因此必须确保 PHP 代码读取和写入的是合适的文件。

有两个重要措施来防止此类问题。
只给 PHP 的 web 用户很有限的权限。
检查所有提交上来的变量。
数据库安全
加密存储模型
SSL/SSH 能保护客户端和服务器端交换的数据，但 SSL/SSH 并不能保护数据库中已有的数据。SSL 只是一个加密网络数据流的协议。
如果攻击者取得了直接访问数据库的许可（绕过 web 服务器），敏感数据就可能暴露或者被滥用，除非数据库自己保护了这些信息。对数据库内的数据加密是减少这类风险的有效途径，但是只有很少的数据库提供这些加密功能。
对于这个问题，有一个简单的解决办法，就是创建自己的加密机制，然后把它用在 PHP 程序内。PHP 有几个扩展库可以完成这个工作，比如说 Mcrypt 和 Mhash 等，它们包含多种加密运算法则。脚本在插入数据库之前先把数据加密，以后提取出来时再解密。有关加密如何工作的例子请参考相关手册。
对某些真正隐蔽的数据，如果不需要以明文的形式存在（即不用显示），可以考虑用散列算法。使用散列算法最常见的例子就是把密码经过 MD5 加密后的散列存进数据库来代替原来的明文密码。参见 crypt() 和 md5()。
SQL 注入
很多 web 开发者没有注意到 SQL 查询是可以被篡改的，因而把 SQL 查询当作可信任的命令。殊不知道，SQL 查询可以绕开访问控制，从而绕过身份验证和权限检查。更有甚者，有可能通过 SQL 查询去运行主机操作系统级的命令。
错误报告
对于 PHP 的安全性来说错误报告是一把双刃剑。一方面可以提高安全性，另一方面又有害。
攻击系统时经常使用的手法就是输入不正确的数据，然后查看错误提示的类型及上下文。这样做有利于攻击者收集服务器的信息以便寻找弱点。比如说，如果一个攻击者知道了一个页面所基于的表单信息，那么他就会尝试修改变量：
过滤检查 白名单机制  黑名单

pre: « 使用 Register Globalsnext: 魔术引号 »
用户提交的数据
要用魔术引号
Warning
本特性已自 PHP 5.3.0 起废弃并将自 PHP 5.4.0 起移除。
没有理由再使用魔术引号，因为它不再是 PHP 支持的一部分。 不过它帮助了新手在不知不觉中写出了更好（更安全）的代码。 但是在处理代码的时候，最好是更改你的代码而不是依赖于魔术引号的开启。 为什么这个功能存在？是为了阻止SQL 注入。 在今天，开发者能够更好得意识到了安全问题，并最终使用数据库转移机制或者 prepared 语句来取代魔术引号功能。
为什么不用魔术引号
Warning
本特性已自 PHP 5.3.0 起废弃并将自 PHP 5.4.0 起移除。
可移植性 编程时认为其打开或并闭都会影响到移植性。可以用 get_magic_quotes_gpc() 来检查是否打开，并据此编程。
性能 由于并不是每一段被转义的数据都要插入数据库的，如果所有进入 PHP 的数据都被转义的话，那么会对程序的执行效率产生一定的影响。在运行时调用转义函数（如 addslashes()）更有效率。 尽管 php.ini-dist 默认打开了这个选项，但是 php.ini-recommended 默认却关闭了它，主要是出于性能的考虑。
不便 由于不是所有数据都需要转义，在不需要转义的地方看到转义的数据就很烦。比如说通过表单发送邮件，结果看到一大堆的 \'。针对这个问题，可以使用 stripslashes() 函数处理。



用 PHP 进行 HTTP 认证
可以用 header() 函数来向客户端浏览器发送“Authentication Required”信息，使其弹出一个用户名／密码输入窗口。当用户输入用户名和密码后，包含有 URL 的 PHP 脚本将会加上预定义变量 PHP_AUTH_USER，PHP_AUTH_PW 和 AUTH_TYPE 被再次调用，这三个变量分别被设定为用户名，密码和认证类型。预定义变量保存在 $_SERVER 数组中。支持“Basic”和“Digest”（自 PHP 5.1.0 起）认证方法。请参阅 header() 函数以获取更多信息。
该行为对于 HTTP 的 Basic 认证标准来说并不是必须的，因此不能依靠这种方法。对 Lynx 浏览器的测试表明 Lynx 在收到 401 的服务端返回信息时不会清空认证文件，因此只要对认证文件的检查要求没有变化，只要用户点击“后退”按钮，再点击“前进”按钮，其原有资源仍然能够被访问。不过，用户可以通过按“_”键来清空他们的认证信息。
为了能够使HTTP工作在 IIS 服务器的 CGI 模式下。 你需要编辑

安全模式uid检查

safe_mode_gid boolean
默认情况下，安全模式在打开文件时会做 UID 比较检查。如果想将其放宽到 GID 比较，则打开 safe_mode_gid。是否在文件访问时使用 UID（FALSE）或者 GID（TRUE）来做检查

