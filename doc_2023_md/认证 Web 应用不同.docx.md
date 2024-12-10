认证 Web 应用不同，RESTful APIs 

通常是无状态的， 也就意味着不应使用 sessions 或 cookies， 因此每个请求应附带某种授权凭证，因为用户授权状态可能没通过 sessions 或 cookies 维护， 常用的做法是每个请求都发送一个秘密的 access token 来认证用户， 由于 access token 可以唯一识别和认证用户， API 请求应通过 HTTPS 来防止 man-in-the-middle（MitM）中间人攻击。
下面有几种方式来发送 access token：
HTTP 基本认证：access token 当作用户名发送，应用在 access token 可安全存在 API 使用端的场景， 例如，API 使用端是运行在一台服务器上的程序。
请求参数：access token 当作 API URL 请求参数发送，例如 https://example.com/users?access-token=xxxxxxxx， 由于大多数服务器都会保存请求参数到日志， 这种方式应主要用于JSONP 请求，因为它不能使用HTTP头来发送access token
OAuth 2：使用者从认证服务器上获取基于 OAuth2 协议的 access token， 然后通过 HTTP Bearer Tokens 发送到 API 服务器。

