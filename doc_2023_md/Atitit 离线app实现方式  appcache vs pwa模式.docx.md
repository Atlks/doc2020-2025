Atitit 离线app实现方式  appcache vs pwa模式

Appcache更加简单

但无法cache数据。。无法实现net first cache策略。。

陷阱 #5：非缓存资源不会加载到缓存页面上#section8
如果您缓存index.html但不缓存cat.jpg，index.html即使您在线，该图像也不会显示。不，真的，这是预期的行为，你自己看看。
要禁用此行为，请使用NETWORK清单的部分
CACHE MANIFEST
# v1index.htmlNETWORK:
*
该*指示浏览器应该允许从缓存页面非缓存资源的所有连接。在这里，您可以看到它应用于上一个示例。显然，这些连接在离线时仍然会失败。
做得好; 您通过简单的发挥其优势的 ApplicationCache 示例完成了它。是的，真的，这就是简单的情况。对不起。让我们尝试一些更艰难的事情

