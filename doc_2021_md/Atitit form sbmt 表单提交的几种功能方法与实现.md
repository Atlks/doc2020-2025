Atitit form sbmt 表单提交的几种功能方法与实现


Atitit 表单提交   mailto协议  http协议


通过电子邮件发送的HTML表单。 在此期间，在共享服务器上很少支持服务器端脚本。为了向网站访问者提供反馈机制，使用了mailto表单。用户填写表单后，单击表单的“提交”按钮，他们的电子邮件客户端将启动并尝试发送包含表单详细信息的电子邮件。 mailto协议的流行和复杂性促使浏览器开发人员将电子邮件客户端整合到他们的浏览器中。[18]


form-urlencoded   multipart/form-data  三种模式


application/x-www-form-urlencoded
multipart/form-data
text/plain
application/json




应用程序/x-www-form-urlencoded
的application/x-www-form-urlencoded内容类型描述了在单个块中发送在HTTP消息体形式的数据。与 GET 请求中 URL 的查询部分不同，数据的长度不受限制。但是，媒体服务器拒绝超过配置参数指定大小的请求MaxFileUploadSize。
此内容类型对于发送包含非 ASCII 字符的大量二进制数据或文本效率低下，并且不允许您上传文件。出于这些目的，Micro Focus建议将数据发送为multipart/form-data（请参阅Multipart/form-data）。
在请求中：
使用等号 ( =)将每个参数与其值分开。
用逗号 ( ,)分隔多个值。
用与号 ( &)分隔每个参数-值对。
Base-64 编码任何二进制数据。
URL 对所有非字母数字字符进行编码，包括 base-64 编码数据中的字符。
多部分/表单数据
在multipart/form-data内容类型中，HTTP 消息体分为多个部分，每个部分包含一个离散的数据部分。
每个消息部分都需要一个标头，其中包含有关该部分数据的信息。每个部分可以包含不同的内容类型；例如，text/plain，image/png，image/gif，或multipart/mixed。如果参数指定多个文件，则必须multipart/mixed在部分标题中指定内容类型。
每个消息部分的编码是可选的。消息部分标头必须指定除默认 (7BIT) 之外的任何编码。
Multipart/form-data 非常适合发送非 ASCII 或二进制数据，并且是唯一允许您上传文件的内容类型。有关表单数据的更多信息，请参阅http://www.w3.org/TR/html401/interact/forms.html。

Ref
Atitit 提交表单的功能h5  js  和 php java的实现
Atitit 发送post http 功能总结

