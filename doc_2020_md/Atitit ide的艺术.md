Atitit ide的艺术

工程管理
编辑功能
自动完成


ide 功能表
转到方法定义:
qt 是ctrl+leftkey,
按住CTRL,move鼠标 over 到 方法上, 出现连结,字体变蓝色的,出现下划线..,..
class  view
method  list
代码片段（Snippet）的功能
 调试
IDE中应当配备调试模块。舍得以前常在DOS命令行下运行开发中的程序，发现错误再切回IDE。现在想想实在是浪费了IDE自带的调试模块。
使用调试模块，首先带来的好处是你不必手工输入命令，也不必在DOS命令行和IDE间切来切去；其次，当遇到错误时，IDE的调试模块会直接显示出错误所在的位置，你不必再去手动寻找。当然调试模块的功能不止于此，具体如何，童鞋们可以自己去深入体会。
在调试方面，Eric6做得更好一些，在遇到错误时，它会自动跳到最终让你出错的位置，省时省力。PyCharm做法略嫌保守，它是在底部的“运行”窗口显示一系列出错的位置，每一个位置带有链接，点击链接即可跳到相应的行。舍得认为，不如在保留链接功能的前提下，自动跳到最后一行出错的位置，通常这一行是问题的关键。如果程序能够做得更智能一些则更好。
版本控制
版本控制也可算是IDE的标配了吧！Eric6和PyCharm都有版本控制的模块，不过舍得认为，PyCharm在这一块做得更细一些，和GibHub结合得很好，舍得用得很趁手。
数据库连接、查看
这项功能只能算是可选配置了。两款IDE都带有数据库内容浏览的功能，它的方便之处在于，我们要查看数据库中某项数据时，可以不必打开专用的数据库管理工具（比如SQLite的SQLite Expert, PostGreSQL的PG Admin，MySQL的PHPMyAdmin等），直接在IDE内查看。
Eric6自带一个内建的SQL浏览器，界面相对简陋，而且每次打开都必须重新设置，不够方便。
PyCharm是通过Database Tools and SQL这款插件来实现数据库连接和查看的功能，用来临时查看一下数据是足够了。
书签
在开发过程中，我们经常需要在一个文档中不同的位置间切换，此时书签功能会给我们带来很大的便利。
两款IDE都有书签功能，PyCharm做得更好一点，它的书签不会因为你退出程序而清除。而Eric6则会在你每次退出程序时，清空你的书签设置。
TODO
舍得在堆代码的时候，想到一些下一步要完善的功能之类的内容时，往往会在文档中插入一行，行首写上“# todo,”，然后把当时的想法写进去。这样日后就能根据todo的标记和内容来逐渐完善自己所开发的软件。
帮助文档
Eric6自带一个WebKit内核的帮助浏览器，当你设置好Python/PyQt/Pyside/Qt等帮助文档的路径后，可以在帮助菜单中直接点击这些文档的链接，Eric6就会调用帮助浏览器来显示这些文档。
PyCharm虽然有一个外部文档的设置和对应的菜单命令，但功能实在太弱比，应该好好完善一下才是。
另外PyCharm虽然提供了一个Search EveryWhere的“强大”功能，但由于搜索结果匹配往往不能尽如人意，使得此功能形如鸡肋。

ref
paip.常见 ide 功能表--用来设计ide以及测试对ide的掌握程度.txt
Python主流IDE对比：Eric VS. PyCharm_舍得_新浪博客.html
