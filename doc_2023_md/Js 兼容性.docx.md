Js 兼容性


Webborwoser ie11 edge mode

Not nullsafe...


Dont arraw fun,,,just anynouse fun is ok
function ()


Import js throw script tag html  
Beir. Node request cant use in htm


No show ex


解决方案：
webBrowser给我们提供了一个属性：ScriptErrorsSuppressed 。当不想再遇到脚本错误时弹出错误提示框，可以将该值设为TRUE。
ScriptErrorsSuppressed 属性的具体的用法如下：
将此属性设置为 false 可调试显示在 WebBrowser 控件中的网页。如果要使用该控件向应用程序添加基于 Web 的控件和脚本代码，则此属性十分有用。如果将该控件用作泛型浏览器，则此属性用处不大。完成应用程序的调试后，将此属性设置为 true 以取消显示脚本错误。
注意：当 ScriptErrorsSuppressed 设置为 true 时，WebBrowser 控件将隐藏其源自基础 ActiveX 控件的所有对话框，而不仅仅是脚本错误。有时，在显示某些对话框（例如，用于浏览器安全设置和用户登录的对话框）时，可能需要取消显示脚本错误。在这种情况下，应将 ScriptErrorsSuppressed 设置为 false，并在 HtmlWindow.Error 事件的处理程序中取消显示脚本错误。


Async   ,,,must sync fun is better
