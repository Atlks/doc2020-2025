Node.js 实现远程桌面监控 
caozhijian 发布于2019-08-23 18:28 / 2973人阅读 
摘要：描述最近使用实现了一个远程桌面监控的应用，分为服务端和客户端，客户端可以实时监控服务端的桌面，并且可以通过鼠标和键盘来控制服务端的桌面。接下来我们要实现远程控制，也就是监听事件，传递事件，执行事件这几部分。
描述 
最近使用node实现了一个远程桌面监控的应用，分为服务端和客户端，客户端可以实时监控服务端的桌面，并且可以通过鼠标和键盘来控制服务端的桌面。
这里因为我是用的同一台电脑，所以监控画面是这样的，当然使用两台电脑一个跑客户端，一个跑服务端才有意义。
原理 
其实这个应用的功能主要分为两部分，一是实现监控，即在客户端可以看到服务端的桌面，这部分功能是通过定时截图来实现的，比如服务端一秒截几次图，然后通过socketio发送到客户端，客户端通过改变img的src来实现一帧帧的显示最新的图片，这样就能看到动态的桌面了。监控就是这样实现的。
另一个功能是控制，即客户端对监控画面的操作，包括鼠标和键盘的操作都可以在服务端的桌面真正的生效，这部分功能的实现是在electron的应用中监听了所有的鼠标和键盘事件，比如keydown、keyup、keypress，mousedown、mouseup、mousemove、click等，然后通过socketio把事件传递到服务端，服务端通过 robot-js来执行不同的事件，这样就能使得客户端的事件在服务端触发了。

