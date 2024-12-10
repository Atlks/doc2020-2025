Atititi 软件界面gui开发之道 attilax著


1. 概览	2
1.1. 编程语言的发展 asm>native>vm>script>dsl	2
1.2. Ui的细化html ,css ,js,分离了布局，外观，与行为。。更加的领域特定了。。细化	3
1.3. 界面ui技术三大分类 native，插件体系，dsl体系	3
1.4. Gui界面语言的趋势，dsl 系列 h5系列	3
2. 起源  20世纪80年代20世纪80年代	4
3. 准则 10大准则	4
4. 应用领域 10大领域	4
5. UI趋势 cli>gui>nui/cui	5
6. 常用的界面ui体系	5
6.1. H5标准与私有ui规范	5
6.2. 俩大模型 dom模型与像素级自绘制	5
6.3. 三大Gui风格体系	6
6.3.1. Page体系  h5	6
6.3.2. Windows体系	6
6.3.3. stage舞台 场景Scene 体系	6
7. 界面控件dom体系	7
7.1. 2 组成部分? 桌面? 视窗? 单一文件界面? 多文件界面? 标签? 菜单? 图标? 按钮	7
7.2. 布局体系  容器类 webkit控件 表单form  winform	7
7.3. 菜单控件 右键菜单，托盘菜单 工具条	7
7.4. 常用控件 文本框，按钮，标签等	7
7.5. 数据控件 表格  树形控件	7
7.6. 多媒体	7
7.7. 其他 托盘图标，文件与文件夹选择 对话框	7
7.8. Icon图标   font icon	7
7.9. H5 体系	7
7.10. 报表与图表	7
8. 布局模式	7
8.1. Flow float	7
8.2. BoxLayout（ html默认布局）	7
8.3. Grid布局 7. CardLayout （tab 布局）	4	8
8.4. 其他	8
9. 报表与图表 （柱状图，饼图，线图趋势图，金字塔，地图，架构图）等	8
9.1. Dom模型 （例如Svg）	8
9.2. 自绘制模式	8
10. Mvc  与服务端ui	9
10.1. 客户端mvc	9
10.2. 渐渐消逝的服务端mvc与服务端ui	9
11. 事件处理与界面逻辑script	9
11.1. Gui线程	9
11.2. 拖放	9
11.3. Js	9
12. 架构体系	9
12.1. Bs cs 桌面  web 移动	9
12.2. 离线Web应用程序	9
13. -----------------其他--------------------------	9
14. 多点触控gui	10
14.1. 包括滑动(swiping),轻按（tapping）,挤压(pinching)及旋转(reverse pinching)。	10
14.2. 加速器 旋转	10
15. 界面自绘 像素体系	10
15.1. 2d paint  GDI+绘图	10
15.2. H5 canvas	10
15.3. Cocos2d	10
16. 特效与动画	10
16.1. 过渡、动画和变换	10
17. Gui常用工具与框架与类库	11
17.1. Dw cs ajax fetch vue jquery	11
17.2. 双向绑定	11
17.3. Swing javafx wpf winform qt h5	11
17.4. 客户端mvc	11
18. 其他	11
18.1. Webkit渲染，	11
18.2. 国际化	11
18.3. 自定义外观　　样式表   子类化 css 	12
19. Plugin体系 插件	12
20. 三维图形	12
20.1.  使用OpenGL绘图  three.js	12
20.2. 使用帧缓存对象生成叠加	12
21. 参考资料	12

概览
编程语言的发展 asm>native>vm>script>dsl
从机器语言，汇编语言到本地native语言(c c++) 到vm语言(java  c#) 再到脚本语言(js php python等) 再到dsl（h5 sql 图像处理halcon matlab）
语言层次越高，可读性一般越好，可移植性越好，不过性能也越差了。。当然如果使用同样的类库的话，只是写点胶水代码的话，差别到是相对来说不大了。

机器语言， 可以说彻底淘汰，唯一的优点就是性能，其他基本全是缺点。。
汇编语言，貌似也基本淘汰，比起机器语言，提升了很大的可读性。。
native语言(c c++) 相对汇编语言可读性又大幅提升，性能方面不如汇编，但比vm语言要高。。。缺点是开发效率，以及可移植性仍然需要提升。。很多图像库貌似都是使用此开发。。依赖于性能的应用大有所为。
vm语言(java  c#)  改进了native语言的问题，增加一个vm层隔离开了os。目前的业界高层应用开发主力
脚本语言 带来更高的生产力。但目前ide的问题，大型复杂企业级开发还难当重任，目前貌似在轻复杂度代码领域比较大发展。
Dsl语言 ，领域特定语言。。比如H5做界面。。Sql做数据库查询。Matlab halcon使用的语言，用来做图像处理。。
更高的开发效率，特别对于特定领域，图像处理，界面，数据库查询等大有优势。。正则表达式，用来文本搜索等。
Dsl语言本身性能很差，但是它如果是调用类库的，类库使用底层语言书写的，所以对性能不影响。


Ui的细化html ,css ,js,分离了布局，外观，与行为。。更加的领域特定了。。细化
界面ui技术三大分类 native，插件体系，dsl体系
Native的就不推荐了，swing winform 安卓 ios native。。
插件体系也没落了，flash  Silverlight Applet 等。。  

Dsl体系正主流。。H5 wpf（xaml）。。但是推荐公有标准化的h5..不推荐wpf了，wpf就是ms的h5。。Java体系基本没有标准化的dsl，只有一些builder框架有一些私有的h5.。。

微信小程序就是腾讯的h5，也是属于一种私有化dsl ，私有化h5

Gui界面语言的趋势，dsl 系列 h5系列
界面是个很专门的领域，需要领域特点语言来做。。   
Dsl系列是目前最好的趋势了。。Dsl里面最好的额就是h5了，跨平台，通用。。

起源  20世纪80年代20世纪80年代
20世纪80年代苹果公司首先将图形用户界面引入微机领域，推出的Macintosh以其全鼠标、下拉菜单操作和直观的图形界面，引发了微机人机界面的历史性的变革。而后微软公司推出了Windows系统，从Windows 3.0发展到Windows 10，使得GUI被应用于用户面更广的个人计算机平台。图形界面的特点是人们不需要记忆和键入繁琐的命令，只需要使用鼠标直接操纵界面。

准则 10大准则
减少用户的认知负担
保持界面的一致性
满足不同目标用户的创意需求
用户界面友好性
图标识别平衡性
图标功能的一致性
建立界面与用户的互动交流
更为人性化的视觉优化
更具识别性的图标及其他元素
更具可操控性和扩充性的使用易用性
更具有企业品牌特色的视觉识别性

应用领域 10大领域
手机通讯移动产品
电脑操作平台
软件产品
PDA产品
数码产品
车载系统产品
智能家电产品
游戏产品
产品的在线推广
网页设计


UI趋势 cli>gui>nui/cui
常用的界面ui体系
H5标准与私有ui规范
form mvc 私有化h5 h5 webpage 
私有化h5  javafx wpf
ASP.NET Form到ASP.NET MVC，最后到AngularJS +Bootstrap，从Windows Forms到WPF。走技术的变更与业务领域结合的路线，一直对.NET开发很有信心。

俩大模型 dom模型与像素级自绘制

三大Gui风格体系

Page体系  h5
Windows体系
stage舞台 场景Scene 体系
展示stage舞台，stage舞台是一个类似于Swing中的JWindow的顶级容器，代表一个窗口。它用于容纳场景Scene，场景Scene是一个类似于Swing的JFrame的容器



界面控件dom体系
2 组成部分? 桌面? 视窗? 单一文件界面? 多文件界面? 标签? 菜单? 图标? 按钮
布局体系  容器类 webkit控件 表单form  winform
菜单控件 右键菜单，托盘菜单 工具条
常用控件 文本框，按钮，标签等
数据控件 表格  树形控件
多媒体
其他 托盘图标，文件与文件夹选择 对话框
Icon图标   font icon
H5 体系
报表与图表
布局模式
Flow float
 BoxLayout（ html默认布局）
Grid布局 7. CardLayout （tab 布局）	4
7. CardLayout （tab 布局）	4

其他
1. 布局的继承结构	1
2. Absoluti 布局（常用）	1
3. Dock、Anchor布局//SpringLayout  (常用)	2
4. Flow 布局（不常用）	2
5. BorderLayout （不常用）	2
6. BoxLayout（ html默认布局）	3
7. CardLayout （tab 布局）	4
8. GridLayout( 不常用)	4
9. GridBagLayout (不常用)	4
10. Fixed 定位（不常用）	4
11. GroupLayout(不推荐)	4
12. 别的布局	5
12.1. DefaultToolBarLayout	5
12.2. MetalRootLayout	5
12.3. JBuilder自带的VerticalFlowLayout	5
12.4. OverlayLayout	5
12.5. RootLayout	5
13. Java的三大的布局:border,flow,grid	6
Anchor布局  	3Dock flow float
Anchor布局  	3Dock flow float


报表与图表 （柱状图，饼图，线图趋势图，金字塔，地图，架构图）等
Dom模型 （例如Svg）
自绘制模式
比如h5 的Canvas，其他语言的gdi

Mvc  与服务端ui
客户端mvc
渐渐消逝的服务端mvc与服务端ui
Jsp jsf jstl wpf aspx等服务端ui
事件处理与界面逻辑script
Gui线程
拖放
Js

架构体系
Bs cs 桌面  web 移动
离线Web应用程序


-----------------其他--------------------------

多点触控gui
用户界面
作。控制方法包括滑动,轻触开关及按键。与系统互动包括滑动(swiping),轻按（tapping）,挤压(pinching)及旋转(reverse pinching)。此外,通过其内置的加速器,可以令其旋转装置改变其y轴以令屏幕改变方向，这样的设计令iPhone更便于使用。

包括滑动(swiping),轻按（tapping）,挤压(pinching)及旋转(reverse pinching)。
加速器 旋转
界面自绘 像素体系
2d paint  GDI+绘图
H5 canvas
Cocos2d

特效与动画
过渡、动画和变换　

Gui常用工具与框架与类库
Dw cs ajax fetch vue jquery
双向绑定
Swing javafx wpf winform qt h5
客户端mvc
其他
Webkit渲染，

国际化
 使用Unicode
　　18.2 让应用程序感知翻译
　　18.3 动态切换语言
　　18.4 翻译应用程序

自定义外观　　样式表   子类化 css

Plugin体系 插件
三维图形
 使用OpenGL绘图  three.js
使用帧缓存对象生成叠加

参考资料
《HTML5权威指南【非常全面详实的网页设计参考书】》(（美）弗里曼 著)【简介_书评_在线阅读】 - 当当图书.html
Atitit gui界面ui技术发展史与未来趋势
《C++ GUI Qt 4编程（第二版）(Trolltech的Qt培训教材，生动、全面、深刻地阐明了Qt程序的设计理念，轻松创建跨平台的解决方案。)》(（加）布兰切特)【简介_书评_在线阅读】 - 当当图书.html
《Java Swing图形界面开发与案例详解》(王鹏)【简介_书评_在线阅读】 - 当当图书.html
《C# WinForm 实践开发教程 (软件职业技术学院“十一五”规划教材)》(钱哨)【简介_书评_在线阅读】 - 当当图书.html
《JavaFX本质论》(（美）安德森)【简介_书评_在线阅读】 - 当当图书.html
atitit.软件开发GUI 布局管理总结java swing wpf web html c++ qt php vOBB.doc











作者:: 常用名：atl  曾用名 ail
绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher  kok  虔诚者Pious 宗教信仰捍卫者 Defender Of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak 
 
简称：： Emir Attilax Akbar 埃米尔 阿提拉克斯 阿克巴
全称：：Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 埃米尔 阿提拉克斯 -阿克巴 - 马哈茂德 - 阿提拉 - 所罗门 - 亚当  阿尔 拉帕努伊

热衷于在it  宗教 哲学 经济学 教育 法学 医学 动植物学 管理 历史 文学 音乐 艺术 军事等各个领域均取得了一定成果

 EMAIL:1466519819@qq.com

