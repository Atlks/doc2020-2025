Atitit 图像处理之编程之类库调用的接口api cli gui ws rest  attilax大总结.docx

1. 为什么需要接口调用？？	1
1.1. 为了方便集成复用模块类库	1
1.2. 嫁接不同的语言与类库，以及嵌入dsl	1
1.3. 方便跨机器，跨开发板，跨硬件，跨运行环境的代码复用	2
2. 接口api的历史	2
2.1. 发展历程	2
2.2. API 这个类库默认提供的接口，要求同语言调用一般	2
2.3. Cli接口 命令行接口。单机跨语言接口（推荐比较常用）	3
2.4. 图形用户接口（GUI），用来调用没有开放其他接口的软件与类库。。比如photoshop等。	3
2.5. Ws接口（不推荐）webserive	3
2.6. Rest接口（推荐，跨机器接口）	3
3. 如何制作接口 使用adapter设计模式	3
3.1. 制作wrap包装接口	3
3.2. 使用包装接口技术，制作api2cli接口。。Cli2rest接口	3
4. 其他接口	4
5. 接口通讯方式：	4
6. 接口的数据交换	4
6.1. 参考资料	5


为什么需要接口调用？？
为了方便集成复用模块类库
比如。我用的xx语言，我要调用其他语言编写的类库怎么办？？？

嫁接不同的语言与类库，以及嵌入dsl
比如图像处理中，我们知道有名的类库opencv halcon matlab等。还有个jhlabs 等类库

编程语言的发展，从机器汇编语言，到native编译语言（c c++) 到 vm编译语言 ( c# java) 到script脚本语言(js python php等) 再到 dsl语言。。

接口使得我们可以分别自由的组合连接各种语言与类库，因为性能因素，类库往往使用性能高的语言编写。调用的时候，使用高层语言又方便快捷。。

方便嵌入dsl，编程语言的趋势dsl。。图像处理是个很专业的领域，适合dsl。。类似的还有界面ui语言h5 ，数据处理sql，图像处理dsl目前halcon matlab用的脚本等。。

方便跨机器，跨开发板，跨硬件，跨运行环境的代码复用
接口api的历史

发展历程
编辑
早在上个世纪的70年代，Digital Research公司的Gary Kildall为微型计算机首创了世界上第一个实用的软件API。这个初生的API大致上有20多个对操作系统的简单函数调用组成，这个操作系统就是CP/M――那时可是相当的简单和粗糙，而同样简单的API却让整个计算机世界发生了重大变化。

随后由比尔·盖茨等开发的MS-DOS操作系统全盘拷贝了CP/M及其API，并在这些API的基础之上又增加了一些简单特性，务实的比尔·盖茨将Kildall的发明变成了巨大的商业应用并立刻让MS-DOS的API在软件开发中占据了主导地位。

在为微软的势力之外，Unix世界也发明了自己的API，这就是TCP/IP，有了它，网络之间就可以自由地通信了。TCP/IP首先在大学里获得了普遍的欢迎

API 这个类库默认提供的接口，要求同语言调用一般
如需跨语言调用，需要提供跨语言的类库wrap包装。。
比如opencv，默认c++接口，还提供了java python的api转接口，就可以默认使用这些语言搞开发。如果js要调用，就不可以直接调用此api了。
Cli接口 命令行接口。单机跨语言接口（推荐比较常用）
Cli接口是个单机跨语言接口，几乎所有语言都支持它。。


 图形用户接口（GUI），用来调用没有开放其他接口的软件与类库。。比如photoshop等。

Ws接口（不推荐）webserive

Rest接口（推荐，跨机器接口）
如何制作接口 使用adapter设计模式
制作wrap包装接口
比如常见的opencv只有c++ java python接口。如果要用js调用怎么办？？可以使用python包装制作一个cli接口即可。。

使用包装接口技术，制作api2cli接口。。Cli2rest接口
就可以实现跨语言，跨机器，跨开发板的，跨运行环境的调用。。
其他接口
Corba接口
Socket 通讯
Ejb（不推荐）
Rim remote
消息队列(Message Queue)


接口通讯方式：

接口基本采用了同步请求/应答方式、异步请求/应答方式、会话方式、广播通知方式、事件订阅方式、可靠消息传输方式、文件传输等通讯方式：
1、同步请求/应答方式：客户端向服务器端发送服务请求，客户端阻塞等待服务器端返回处理结果；
2、异步请求/应答方式：客户端向服务器端发送服务请求，与同步方式不同的是，在此方式下，服务器端处理请求时，客户端继续运行；当服务器端处理结束时返回处理结果；
3、会话方式：客户端与服务器端建立连接后，可以多次发送或接收数据，同时存储信息的上下文关系；
4、广播通知方式：由服务器端主动向客户端以单个或批量方式发出未经客户端请求的广播或通知消息，客户端可在适当的时候检查是否收到消息并定义收到消息后所采取的动作；
5、事件订阅方式：客户端可事先向服务器端订阅自定义的事件，当这些事件发生时，服务器端通知客户端事件发生，客户端可采取相应处理。事件订阅方式使客户端拥有了个性化的事件触发功能，极大方便了客户端及时响应所订阅的事件；
6、文件传输：客户端和服务器端通过文件的方式来传输消息，并采取相应处理；
7、可靠消息传输：在接口通讯中，基于消息的传输处理方式，除了可采用以上几种通讯方式外，还可采用可靠消息传输方式，即通过存储队列方式，客户端和服务器端来传输消息，采取相应处理。

接口的数据交换
一般通过cli的标准io流即可。。
或者json交换。
或者文件交换。。
或者通过数据库交互。
通过消息网关也可。

参考资料

系统接口规范以及常见的接口技术概述和比较 - Dake - 博客频道 - CSDN.NET

Atitit 使用h5技术( html css js)制作桌面程序gui界面解决方案attilax总结


1.1. 理解Atwood定律	1
1.2. H5做出个html的ui是很方便的，跨平台	2
1.3. 启动exe。。使用chrome 的app模式启动即可	2
1.4. Js ide使用webstorm，支持js单点调试	3
1.5. 使用ajax技术连接界面ui与后端	3
1.6. H5技术调用本地文件选择对话框	4
1.7. 结论，使用javascript技术制作桌面gui程序已经比较成熟了。但是依然有一些小坑	6


理解Atwood定律
在Jeff Atwood发表于2007年的这篇博客里，他提出了著名的“Atwood定律”，即”任何能够用JavaScript实现的应用系统，最终都必将用JavaScript实现。“ （Any application that can be written in JavaScript, will eventually be written in JavaScript.

这应该就是Jeff Atwood定律的由来：JavaScript既能独立完成所有互联网应用所需的功能开发，同时又是主流编程语言中最为轻量级的

编程语言的可读性与开发效率提升，也是从机器语言>>asm汇编》》native类型语言(vb pb c c++ delphi) >>vm类型语言(java c#) >>script脚本语言(js python php) >>dsl类型语言(halcon matlab h5  autoit shell sql脚本等）。。

脚本语言和dsl在GUI领域一个非常好的一个选择，主流脚本基本语言有js python  php等，当然还要集大成者h5。。Attilax更加的看好js ，python的缩进很蛋疼。。脚本语言最大的优点就是不用编译啊，方便修改，体积小巧。部署友好性较好。。



H5做出个html的ui是很方便的，跨平台
但是还是有一些坑要填的啊。。特此记录。。

H5 的ui方面的ide就是dw了。。我用的dreamweaver cc 2015版本还不错
H5方面的资源就很多了，浩如烟海，这里我使用jq操作dom，使用bootstrap这个css框架稍微美化下界面



启动exe。。使用chrome 的app模式启动即可
以往我们桌面gui程序使用h5做界面，需要使用webkit browser控件作为主控件，比如c#.net的wpf，或者java的javafx，还是有些麻烦的。。

现在，经过我孜孜不倦的研究，使用chrome这些浏览器的app模式即可啊。。现在的浏览器功能真是越来越强大了啊。。
如果全屏程序，全屏模式：kiosk

启动命令  C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chrome.exe --app=http://localhost:8088/imgSearch/imgSearch.html

效果如下图，和使用javafx技术制作桌面gui程序是一模一样的。。




Js ide使用webstorm，支持js单点调试
后端的js调试使用这个ws。。前段js调试使用chrome的开发者工具即可了。。。
使用ajax技术连接界面ui与后端
还有一种浏览器扩展对象技术，可以直接连接后端，单貌似不好调试。。也许是我研究的不够。。
使用ajax技术连接后端有个好处就是方便调试，毕竟chrome这些浏览器的debug工具很强大的。
不过使用ajax，就得要一个web server了。这里直接使用nodejs +express web模块

var path = require('path');
var express = require('express');
var app = express();
console.log("__dirname:"+__dirname)
webroot=path.join(__dirname, '..');
console.log("webroot:"+webroot)

//return;

app.use(express.static(webroot));

app.get('/', function(req, res) {
    res.send('Hello world');
});


var server = app.listen(8088, function() {
    console.log('Express is listening to http://localhost:8088');
});

H5技术调用本地文件选择对话框
默认h5是不能调用本地文件路径的。。所以我们使用ajax技术后端调用即可。。不过，js貌似比较难以直接调用os的api。。还好，使用cli接口调用一个exe打开文件选择框即可。。。这个exe文件使用autoit脚本即可制作。。Autoit是个调用os功能的很好的dsl，其次使用shell脚本也是个调用os功能的强大dsl。。。
这样就可以直接打开本地的文件筐了









确认后，会把本地路径显示到文本框里面去


function  main() {
    $("#openTmpPic").click(function () {
        //note must add ati  ext ...beir   backcall/?xxxx
        $.get("../backcall.ati", {cls: null, meth: "openTmpPic", p1: "v1", p1_type: "int", rdm: Math.random()}, function (arry) {
                    $("#tmppath").val(arry);
        });

    });

在nodejs后端，增加一个调用即可

app.get('/backcall.ati', function(req, res) {
 //   reqG=
    var meth=req.query.meth;
    eval(meth+"(req,res)");
    var p1=req.query.p1
    console.log("---p:"+p1);
 //   res.send('Hello world');
});
 function openTmpPic(req, res)
{
    var fsrMode = require("../com.attilax/ui/FileSelector.js");
    var fsr=new fsrMode.FileSelector();
    fsr.folderSelector(function(path){
        res.send(path);
    })
}

结论，使用javascript技术制作桌面gui程序已经比较成熟了。但是依然有一些小坑
比如调用os的api，。稍微麻烦些。还好可以通过cli接口调用autoit ，shell等os dsl来解决。。
js目前不能直接调用dll貌似。貌似有时候还得通过调用autoit来解决。。
其次，一些类库比如opencv对js的支持还不够，需要通过py来中转。。

作者:: 绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher  kok  虔诚者Pious 宗教信仰捍卫者 Defender Of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak 万兽之王
简称：： Emir Attilax Akbar 埃米尔 阿提拉克斯 阿克巴
全名：：Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 埃米尔 阿提拉克斯 阿克巴 本 马哈茂德 本 阿提拉 本 所罗门 本亚当  阿尔 拉帕努伊
常用名：atl（ail），  EMAIL:1466519819@qq.com


头衔：uke总部o2o负责人，全球网格化项目创始人，
uke宗教与文化融合事务部部长， uke宗教改革委员会副主席
Emir Uke部落首席大酋长，
uke制度与重大会议委员会委员长，uke保安部首席大队长,uke制度检查委员会副会长， 
uke 首席cto  奶牛科技首席cto ， 软件部门总监 技术部副总监  研发部门总监主管  产品部副经理 项目部副经理
uke波利尼西亚区大区连锁负责人 汤加王国区域负责人 uke克尔格伦群岛区连锁负责人，莱恩群岛区连锁负责人，uke布维岛和南乔治亚和南桑威奇群岛大区连锁负责人 
 Uke软件标准化协会理事长理事长 Uke 数据库与存储标准化协会副会长 
 
uke终身教育学校副校长   Uke医院 与医学院方面的创始人
 Uke 户外运动协会理事长  度假村首席大村长  uke交友协会会长 
 uke出版社编辑总编

转载请注明来源：attilax的专栏  ?http://blog.csdn.net/attilax
--Atiend  v4



