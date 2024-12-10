Login功能的最佳实践


可以用 header() 函数来向客户端浏览器发送“Authentication Required”信息，使其弹出一个用户名／密码输入窗口。当用户输入用户名和密码后，包含有 URL 的 PHP 脚本将会加上预定义变量 PHP_AUTH_USER，PHP_AUTH_PW 和 AUTH_TYPE 被再次调用，这三个变量分别被设定为用户名，密码和认证类型。预定义变量保存在 $_SERVER 数组中。支持“Basic”和“Digest”（自 PHP 5.1.0 起）认证方法。请参阅 header() 函数以获取更多信息。



使用 PHP 进行 HTTP 身份验证¶
可以使用 header()函数向客户端浏览器发送"Authentication Required" 消息，使其弹出用户名/密码输入窗口。用户填写用户名和密码后，将再次调用包含 PHP 脚本的 URL，并将 预定义变量 PHP_AUTH_USER、PHP_AUTH_PW和AUTH_TYPE分别设置为用户名、密码和身份验证类型。这些预定义变量可在$_SERVER数组中找到。仅支持“基本”和“摘要”身份验证方法。有关详细信息， 请参阅 header()函数。

