
序言
. MVC是 推出的一项具有现代软件设计思想的Web应用程序开发技术，如今已经演化到. MVC 3版本，而且. MVC 4也即将发布。它让众多的平台开发人员能够以一种更好的软件设计方法学在.平台上从事Web应用程序的开发。正如作者所指出的：它整合了“模型-视图-控制器（MVC）”体系结构的效率与简洁、敏捷开发最现代的思想与技术、以及当前.平台最好的部分。它是传统的. Web表单（Web Form）的一种完善的替代品。
《Pro . MVC 3  》是为数不多的系统介绍. MVC技术书籍中的一本好书。作者attilax atl  ，以及技术评论员 ，既是经验丰富的IT专家，也是高水平的专业技术作家，他们知道如何写书，更知道如何介绍专业技术。本书严谨、清晰、深入、细致且广泛地介绍了. MVC方方面面的技术。书中充满了技术性和学术性，语言流畅、说理透彻，且示例详实，并为软件开发人员探究. MVC奥秘提供了无尽的线索。阅读此书不仅能学到. MVC的完整技术，还能从中体会作者科学的软件设计思想和严谨踏实的工作作风。
. MVC的推出时间不短了，但该项技术的高端资料目前还很缺乏，尤其是系统介绍该项技术的中文书籍几乎为空白。在我们，在.平台上从事开发的人员众多，. MVC代表着 推出的一项优秀开发技术，并将是今后很长一段时期内在.平台上从事Web开发的主流技术。的开发人员，尤其是以往在.平台上运用Web Form从事软件开发的人员，需要尽快学习和掌握. MVC开发技术，并从Web Form尽快转入MVC开发行列。只有这样，才能跟上世界软件技术发展的步伐，以更好的软件设计方法学为的信息化事业服务。但是，在众多的软件开发人员中，毕竟有很大一部分人英文水平尚有欠缺，也有很大一部分年青人将要步入软件开发行业，即使是英文有相当基础的人，阅读中文资料也会有更快的速度和更深的理解。为此，我们挑选了这本，以期让更多的国人能更快更好地掌握该项技术。
全书分为三大部分共23章，第一部分（第1-9章）系统介绍了. MVC的背景知识、基本思想和基本概念，并以一个实用的应用程序为例，详细介绍了MVC各个部分的基本实现方法和思想。第二部分（第10-20章）对MVC相关的主要技术细节分别作了详细的描述，使读者大有登堂入室之感。第三部分（第21-23章）则介绍了MVC相关的一些外围技术，包括系统安全性、认证与授权，以及应用程序部署等。本书的全部文字 最终定稿由 完成， 老师承担了本书的全部 校对和文字修订工作。
本书 版能够出版发行，首先要感谢本书的作者，是他们为我们著作了一本好书。其次要感谢 xx出版社引进了本书的 授权，使我们获得了 此书的机会，并实现将其介绍给 广大读者的良好愿望。也借此机会向本书的技术审核，徐滔先生，致以崇高的敬意，他使本书的质量与水平大大向前迈进了一步。此外，特别要感谢本书的责任编辑   先生，他以巨大的热情和高度的责任心为本书的出版做了大量繁琐细致的出版业务工作和联络工作。也要感谢众多的排版与编印人员，是他们的辛勤劳动才得以使本书付诸印刷出版。还要感谢众多的网友，包括bbsMVC论坛的朋友和博客园的广大园友，他们为本书的撰写提出了很多十分宝贵的意见和建议。没有他们的无私奉献，让本书走到今天这一步是不可能的。在此，作者对所有为此书的出版做出过贡献的人表示深深的感谢和崇高的敬意！
本书对 的错误之处作了一些修正，在 难懂或需要提醒的地方添加了一些 说明。尽管我们在 过程中力图做得更好，但终会因个人的业务水平、英文水平，乃至中文文学水平的欠缺，以及 过程中的粗心和不够严谨，本书 版必然存在很多错误、不足和不当之处。恳请读者在阅读过程中少一些谴责，也热切期望读者对本书提出宝贵意见、建议和勘误，并欢迎与作者者进行联络（ ）。



Atitit mvc之道 mvc的艺术 书稿草案 v1 t11

Capt1 第一章mvc的几大概念
Capt1  mvc的几大概念

目录
1. 历史发展	1
2. Dispatcher   Controller	2
2.1. DispatcherServlet主要用作职责调度工作，本身主要用于控制流程，主要职责如下：	2
2.2. DispatcherServlet初始化主要做了如下两件事情：	2
2.3. DispatcherServlet默认使用WebApplicationContext作为上下文，该上下文中特殊的Bean有：	3
3. 声明式渲染	4
3.1. 命令式渲染：实现过程按照逻辑过程写出来的。（不仅要关注结果，还有过程）	4
3.2. 条件与循环	4
3.3. 用组件构建（应用）	5
4. 框架模式有哪些？框架和设计模式的区别框架、设计模式这两个概念总容易	5
5. 特点 优缺点	5
5.1.1. 优点	5
5.1.2. 缺点	7

CAPT2 第二章路由和导航

目录
1. 路由”一般可以概述为起点到通往目的地的路径	1
1.1. 分类 web路由 vs 网络路由	1
1.2. 静态路由　vs 　第4章　动态路由	1
2. 路由历史	2
2.1. 后端路由： 浏览器在地址栏中切换不同的url时，	2
2.2. 前端路由：	3
3. 前端路由目前主要有两种方法：	3
3.1. 1、利用url的hash,就是常用的锚点（#）操作，	3
3.2. 2、利用HTML5的History模式，	3
4. 前端路由实现	4
4.1.1. 1.Pjax（PushState + Ajax）	4
4.1.2. 2.Hjax（Hash + Ajax）	4
5. 高级路由部分知识	5
6. Atitit mvc路由静态文件读取输出	5
6.1. 大概步骤原理	5
6.2. 拦截器概念	5
6.3. Filter	6
6.4. Code  /springboothelloword/src/springboothtml/HtmlWebserverFilter.java	7
7. Atitit  mvc框架的实现 mvc的原理demo v2 sbb.docx	8
8. Atitit 导航模式 面包屑  胶囊式 标签式tab	8
9. Ref	9





Capt4 第四章格式化与转换器

目录
1. 几种常见需要格式化的数据	2
1.1. 财富的格式	3
1.2. 小数的格式化展示	3
1.3. JXML进行格式化排版,	3
1.4. 时间的格式	3
1.5. 代码格式化	3
1.6. 字符串5 fmt	3
1.7. 国际化的支持	3
1.8. Title tool long substr	3
1.9. Img use servlet read.src	3
1.10. 富文本格式化	3
1.11. HTML 文本格式化实例	3
2. printpretty   技术	4
2.1. 代码着色	4
2.2. 语法高亮	4
2.3. 布局算法	4
3. 过滤器  格式化 Converter和Formatter	4
3.1. 国际化	4
4. -------------------------------------------------	5
5. atitit.日期,星期,时候的显示方法ISO 8601标准	5
6. ISO 8601	5
7. 年度显示表示法	5
8. DAte日期的显示	6
8.1. Normal	6
8.2. 顺序日期表示法(可以将一年内的天数直接表示)	6
8.3. 星期显示法(可以用2位数表示年内第几个日历星期，再加上一位数表示日历星期内第几天)	6
9. 时间表示法(对UTC时间最后加一个大写字母Z，其他时区用实际时间加时差表示)	7
10. 日期和时间的组合表示法(要在时间前面加一大写字母T)	7
11. 时间段表示法	7
11.1. 重复时间表示法	7
12. --------------------------------------------	8
13. 国际化之道	8
14. 组成部分	8
14.1. 姓名，地址等特殊信息 	8
14.2. 图标的通用性 	8
14.3. 声音使用 	8
14.4. 颜色使用 	8
14.5. 键盘差别 	9
14.6. 政治因素 	9
14.7. 时间日期格式	9
14.8. atitit.国际化---货币支持_2.doc	9
15. 技术实现	9
15.1. 两项软件技术起着重大作用 Unicode标准和独立本地化资源文件的技术（single world-wide binary）	9
15.2. 本地化资源文件技术	9
15.3. 文字翻译、	10
15.4. 多字节字符集支持 Unicode标准	10
15.5. 、用户界面重新设计和调整、本地化功能增强与调整、	10
15.6. 桌面排版(DTP)、	10
15.7. 编译、测试	10
15.8. .    翻译记忆（TM）和计算机辅助翻译（CAT）是软件本地化的语言技术	10
16. Ref	10


