Atiitt 知识图谱的艺术  atl著 v3 t55.docx
Atiitt 知识图谱的艺术  atl著




二、知识图谱  知识图谱本质上是结构化的语义知识库，是一种由节点和边组成的图数据结构，

知识图谱本质上是结构化的语义知识库，是一种由节点和边组成的图数据结构，以符号形式描述物理世界中的概念及其相互关系，其基本组成单位是“实体—关系—实体”三元组，以及实体及其相关“属性—值”对。不同实体之间通过关系相互联结，构成网状的知识结构。在知识图谱中，每个节点表示现实世界的“实体”，每条边为实体与实体之间的“关系”。通俗地讲，知识图谱就是把所有不同种类的信息连接在一起而得到的一个关系网络，提供了从“关系”的角度去分析问题的能力。

知识图谱可用于反欺诈、不一致性验证、组团欺诈等公共安全保障领域，需要用到异常分析、静态分析、动态分析等数据挖掘方法。特别地，知识图谱在搜索引擎、可视化展示和精准营销方面有很大的优势，已成为业界的热门工具。但是，知识图谱的发展还有很大的挑战，如数据的噪声问题，即数据本身有错误或者数据存在冗余。随着知识图谱应用的不断深入，还有一系列关键技术需要突破
--------------------- 

与传统知识表示的区别

 

理解今天的知识图谱内涵，是不能割裂其历史脐带的。上世纪七八十年代的各种知识表示与我们今天的知识图谱到底有着本质差别。传统语义网络与知识图谱的差别首先表现在其规模上。

 

知识图谱是一种大规模语义网络，与上世纪七八十年代的各类语义网络相比较，最显著的差异就是规模差异。推而广之，以知识图谱为代表的大数据时代的各种知识表示与传统的知识表示的根本差别首先体现在规模上。传统知识工程一系列知识表示都是一种典型的“小知识”（smallknowledge）。

 

而到了大数据时代，受益于海量数据、强大计算能力以及群智计算，我们如今能够自动化构建、或者众包构建大规模、高质量知识库，形成所谓的“大知识”(bigknowledge，合肥工业大学的吴兴东教授在很多场合下也提到类似观点)。所以知识图谱与传统知识表示在浅层次上的区别，就是大知识与小知识的差别，是在规模上的显而易见的差别。

 

更深刻地进行分析就会发现，这样的一个知识规模上的量变带来了知识效用的质变。

 

知识工程到了上世纪八十年代之后就销声匿迹了。根本原因在于传统知识库构建主要依靠人工构建、代价高昂、规模有限。举个例子，我国的词林辞海是上万名专家花了10多年编撰而成的，但是它只有十几万词条。而现在任何一个互联网上的知识图谱，比如DBpedia，动辄包含上千万实体。人工构建的知识库虽然质量精良，但是规模有限。有限的规模使得传统知识表示难以适应互联网时代的大规模开放应用的需求。
--------------------- 


知识图谱的重要性
 
知识图谱是实现机器认知智能的基础。机器认知智能的两个核心能力：“理解”和“解释”，均与知识图谱有着密切关系。首先需要给机器“理解与解释”提出一种解释。我认为机器理解数据的本质是建立起从数据到知识库中的知识要素（包括实体、概念和关系）映射的一个过程。

过程的本质就是将知识库中的知识与问题或者数据加以关联的过程。有了知识图谱，机器完全可以重现我们的这种理解与解释过程。有过一定计算机研究基础的，是不难完成上述过程的数学建模的。知识图谱对于机器认知智能的重要性也体现在下面几个具体方面。

 

▌2.1 知识图谱使能机器语言认知

 

知识图谱对机器认知智能的必要性还可以从若干具体问题来进行阐述。首先，我们来看机器认知的核心能力之一：自然语言理解。

 

我的观点是机器理解自然语言需要类似知识图谱这样的背景知识。自然语言是异常复杂的：自然语言有歧义性、多样性，语义理解有模糊性且依赖上下文。机器理解自然语言困难的根本原因在于，人类语言理解是建立在人类的认知能力基础之上的，人类的认知体验所形成的背景知识是支撑人类语言理解的根本支柱
--------------------- 
机器自然语言理解所需要的背景知识是有着苛刻的条件的：规模足够大、语义关系足够丰富、结构足够友好、质量足够精良。

 

以这四个条件去看知识表示就会发现，只有知识图谱是满足所有这些条件的：知识图谱规模巨大，动辄包含数十亿实体；关系多样，比如在线百科图谱DBpedia包含数千种常见语义关系；结构友好，通常表达为RDF三元组，这是一种对于机器而言能够有效处理的结构；质量也很精良，因为知识图谱可以充分利用大数据的多源特性进行交叉验证，也可利用众包保证知识库质量。所以知识图谱成为了让机器理解自然语言所需的背景知识的不二选择。

 

▌2.3 知识图谱使能可解释人工智能

 

知识图谱对于认知智能的另一个重要意义在于：知识图谱让可解释人工智能成为可能。

 

“解释”这件事情一定是跟符号化知识图谱密切相关的。因为解释的对象是人，人只能理解符号，没办法理解数值，所以一定要利用符号知识开展可解释人工智能的研究。可解释性是不能回避符号知识的。
--------------------- 
4 知识引导将成为解决问题的主要方式

 

 知识图谱的另一个重要作用体现在知识引导将成为解决问题的主要方式。
前面已经多次提及用户对使用统计模型来解决问题的效果越来越不满意了，统计模型的效果已经接近“天花板”，要想突破这个“天花板”，需要知识引导。

 

举个例子，实体指代这样的文本处理难题，没有知识单纯依赖数据是难以取得理想效果的。比如“张三把李四打了，他进医院了”和“张三把李四打了，他进监狱了”，人类很容易确定这两个不同的“他”的分别指代。因为人类有知识，有关于打人这个场景的基本知识，知道打人的往往要进监狱，而被打的往往会进医院。但是当前机器缺乏这些知识，所以无法准确识别代词的准确指代。很多任务是纯粹的基于数据驱动的模型所解决不了的，知识在很多任务里不可或缺。比较务实的做法是将这两类方法深度融合。

 

▌2.5 知识将显著增加机器学习能力

 

知识对于认知智能又一个很重要的意义就是将显著增强机器学习的能力。

 

当前的机器学习是一种典型的“机械式”学习方式，与人类的学习方式相比显得比较笨拙。我们的孩童只需要父母告知一两次：这是猫，那是狗，就能有效识别或者区分猫狗。而机器却需要数以万计的样本才能习得猫狗的特征。

 

我们中国人学习英语，虽然也要若干年才能小有所成，但相机器对于语言的学习而言要高效的多。机器学习模型落地应用中的一个常见问题是与专家知识或判断不符合，这使我们很快陷入进退两难的境地：是相信学习模型还是果断弃之？机器学习与人类学习的根本差异可以归结为人是有知识的且能够有效利用知识的物种。
--------------------- 
识图谱系统的生命周期包含四个重要环节：知识表示、知识获取、知识管理与知识应用。这四个环节循环迭代。

 

知识应用环节明确应用场景，明确知识的应用方式。

 

知识表示定义了领域的基本认知框架，明确领域有哪些基本的概念，概念之间有哪些基本的语义关联。比如企业家与企业之间的关系可以是创始人关系，这是认知企业领域的基本知识。知识表示只提供机器认知的基本骨架，还要通过知识获取环节来充实大量知识实例。比如乔布斯是个企业家，苹果公司是家企业，乔布斯与苹果公司就是“企业家-创始人-企业”这个关系的一个具体实例。
--------------------- 
就是知识管理。这个环节将知识加以存储与索引，并为上层应用提供高效的检索与查询方式，实现高效的知识访问。

 知识表示

 

在知识表示方面，常用三元组（主语、谓词、宾语）表示知识图谱。如三元组<七里香，歌曲原唱，周杰伦>表示“七里香这首歌曲的原唱是周杰伦”这一知识。需要强调一点，知识图谱只能表达一些简单的关联事实，但很多领域应用的需求已经远远超出了三元组所能表达的简单关联事实，实际应用日益对于利用更加多元的知识表示丰富和增强知识图谱的语义表达能力提出了需求。
--------------------- 
增强知识图谱的跨媒体语义表示。

 

当前的知识图谱主要以文本为主，但是实际应用需要有关某个实体的各种媒体表示方式，包括声音、图片、视频等等。比如对于实体“Tesla Model S”，我们需要将其关联到相应图片和视频。知识图谱时空维度拓展在物理实现上可以通过定义四元组或者五元组加以实现。跨媒体表示可以通过定义相关的属性加以实现。知识图谱的语义增强总体上而言将是未来一段时间知识表示的重要任务。知识图谱作为语义网络，侧重于表达实体、概念之间的语义关联，还难以表达复杂因果关联与复杂决策过程。

 

如何利用传统知识表示增强知识图谱，或者说如何融合知识图谱与传统知识表示，更充分地满足实际应用需求，是知识图谱领域值得研究的问题之一。在一些实际应用中，研究人员已经开始尝试各种定制的知识表示，在知识图谱基础上适当扩展其他知识表示是一个值得尝试的思路。
--------------------- 
 原创文章，转载请附上博文链接！

.3 知识管理
 
知识图谱的管理主要图谱的存储、检索等问题。通常这些问题的解决需要数据库系统的支撑，因而系统的选型也是知识图谱管理的一个重要问题。这里主要讨论能用于知识图谱管理的数据库系统选型以及知识图谱查询语言。知识图谱存储是个较为专业化的问题


构建知识图谱的方法
关联拓展知识点横向拓展
纵向拓展，向上拓展，，向下向内拓展知识点
更有深度和广度

Atitti 知识图谱构建方法attilax 总结

1.1. 知识图谱schema构建(体系化)	1
1.2. 纵向垂直拓展（向上抽象，向下属性拓展）	2
1.3. 横向拓展	2
1.4. 网拓展	2
1.5. a) 推理	2
1.6. c) 相关实体挖掘	2
2. other	3
2.1. 面向站点的包装器（Site-specificWrapper）	3
2.2. 5. 知识图谱的更新和维护	3

1. 2. 知识图谱的数据来源	1
1.1. a) 百科类数据	2
1.2. b) 结构化数据	3
1.3. 各种半结构化数据（形如HTML表格）抽取相关实体的属性-值对来丰富实体的描述	3
1.4. d) 通过搜索日志进行实体和实体属性等挖掘	4


知识图谱面临的挑战

 

知识图谱技术的挑战主要表现在知识表示、知识获取和知识应用等三个方面。

 

在知识表示层面，越来越多的领域应用不仅仅需要关联事实这种简单知识表示，还要表达包括逻辑规则、决策过程在内的复杂知识；需要同时表达静态知识和动态知识。单单知识图谱已经不足以解决领域的很多实际问题。如何去增强知识图谱的语义表达能力，如何综合使用多种知识表示来解决实际应用中的复杂问题是非常重要的研究课题。

 

在知识获取方面，领域知识图谱一般样本很小，如果需要构建抽取模型，那就需要基于小样本构建有效的模型。目前基于小样本的机器学习仍然面临巨大挑战。解决这一问题的思路之一就是利用知识引导机器学习模型的学习过程。具体实现手段已经有不少团队在开展相关的探索工作，比如利用知识增强样本、利用知识构建目标函数的正则项以及利用知识构建优化目标的约束等等。总体而言，这仍然是个开放问题需要巨大的研究投入。

 

在知识的深度应用方面。如何将领域知识图谱有效应用于各类应用场景，特别是推荐、搜索、问答之外的应用，包括解释、推理、决策等方面的应用仍然面临巨大挑战，仍然存在很多开放性问题。

 

六、知识图谱未来的发展趋势

 

从2012年发展至今，知识图谱技术发生了一系列的变革。从两个方面来讲，一方面是应用场景，另一个方面就是技术生态。随着应用场景和技术生态的变化，整个知识图谱面临着全新的挑战，以前的技术手段在应对现在智能化大潮给我们提出的挑战的时候，已经有些力不从心，所以我们要研发一些新技术。

 

从应用的角度来讲，知识图谱的应用趋势越来越从通用领域走向行业领域，现在的局面是通用与行业应用百花齐放，各行各业都在讨论适合自己的知识图谱。
--------------------- 
 常见使用的技术
常见知识图谱的处理技术
爬取、深度提取和挖掘和知识图谱  存储与管理 的高效查询与挖掘分析；

文本处理的基本算法与概念
语料数据处理
常用的公开知识图谱如DBpedia, Freebase, Yago，Openkg等


爬虫与web抓取
半结构化分析（html word pdf文档分析
表单填充(Form Filling)技术
在线机器人技术
验证码识别
ref
知识图谱res资源包\.？知识图谱的数据来源.docx.placehold
知识图谱res资源包\2.?知识图谱的数据来源.docx
知识图谱res资源包\2.?知识图谱的数据来源.docx.txt
知识图谱res资源包\Atitit  补充说明 sql知识图谱与线路图attilax总结补充说明.docx.txt
知识图谱res资源包\Atitit learn by need 需要的时候学与预先学习知识图谱路线图.docx.txt
知识图谱res资源包\atitit v9图像处理 知识图谱 知识网络 知识点 kngraph knnet  attilax总结   r1e - 副本.xlsx
知识图谱res资源包\atitit v9图像处理 知识图谱 知识网络 知识点 kngraph knnet  attilax总结   r1e.xlsx
知识图谱res资源包\Atitit 一个完整的体系架构，知识图谱，路线图，科技树，思维导图 结构图.docx
知识图谱res资源包\Atitit 一个完整的体系架构，知识图谱，路线图，科技树，思维导图 结构图.docx.txt
知识图谱res资源包\Atitit 个性化推荐算法；相关知识挖掘 知识图谱挖掘.docx
知识图谱res资源包\Atitit 个性化推荐算法；相关知识挖掘 知识图谱挖掘.docx.txt
知识图谱res资源包\Atitit 农历日历的算法以及attilax总结的知识图谱 .docx.txt
知识图谱res资源包\Atitit 农历日历的算法以及attilax总结的知识图谱 .docx.txt.txt
知识图谱res资源包\Atitit 图像处理知识点  知识体系 知识图谱 v2.docx.txt
知识图谱res资源包\Atitit 图像处理知识点  知识体系 知识图谱.docx.txt
知识图谱res资源包\Atitit 图像处理知识点体系知识图谱 路线图attilax总结 v4 qcb.docx.txt
知识图谱res资源包\Atitit 图像处理科技树 知识图谱 补充.docx.txt
知识图谱res资源包\atitit 摄像头与onvif与流媒体 知识图谱网络 科技树 架构体系 ipc stream media knmap techtree v2qc27.xlsx.txt
知识图谱res资源包\Atitit 知识图谱 与知识体系的分类.docx
知识图谱res资源包\Atitit 知识图谱 与知识体系的分类.docx.txt
知识图谱res资源包\Atitit 知识图谱的用途.docx
知识图谱res资源包\Atitit 知识图谱的用途.docx.txt
知识图谱res资源包\Atitit 知识图谱知识架构体系的构建---定向抓取法.docx
知识图谱res资源包\Atitit 知识图谱知识架构体系的构建---定向抓取法.docx.txt
知识图谱res资源包\Atitit 知识图谱解决方案：提供完整知识体系架构的搜索与知识结果.docx
知识图谱res资源包\Atitit 知识图谱解决方案：提供完整知识体系架构的搜索与知识结果.docx.txt
知识图谱res资源包\Atitit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx(1).txt.txt
知识图谱res资源包\Atitit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx.txt.txt
知识图谱res资源包\Atitit 项目管理--团队建设知识图谱mybatis知识点体系结构.docx.txt
知识图谱res资源包\Atitit 项目管理--团队建设知识图谱mybatis知识点体系结构.docx.txt.txt
知识图谱res资源包\Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取 (2).docx
知识图谱res资源包\Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取 (3).docx
知识图谱res资源包\Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx
知识图谱res资源包\Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx (2).txt
知识图谱res资源包\Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx.txt
知识图谱res资源包\Atitti 知识图谱构建方法attilax 总结.docx
知识图谱res资源包\Atitti 知识图谱构建方法attilax 总结.docx.txt
知识图谱res资源包\Attiti 软件工程知识图谱attilax总结.docx.txt
知识图谱res资源包\c all、r71 doc ntpc、设计文档、atitit v8图像处理 知识图谱 知识网络 sysmap  attilax总结 v8 r1d.xlsx.index.txt
知识图谱res资源包\c、005 r2c、00onvif_ws_wbsvs、Atitit 一个完整的体系架构，知识图谱，路线图，科技树，思维导图 结构图.docx.index.txt
知识图谱res资源包\c、005 r2c、00onvif、atitit 摄像头与onvif与流媒体 知识图谱网络 科技树 架构体系 ipc stream media knmap techtree v2qc27.xlsx.index.txt
知识图谱res资源包\c、doc r1 home、000qc31、atitit zip rar文件名列表提取 知识图谱 科技树.xlsx.index.txt
知识图谱res资源包\c、doc r1 home、000r19、atitit 架构知识图谱知识网络.xlsx.index.txt
知识图谱res资源包\c、doc r1 home、000r1b、atitit v8图像处理 知识图谱 知识网络 sysmap  attilax总结 v8 r1d.xlsx.index.txt
知识图谱res资源包\c、doc r1 home、000r1e、atitit v9图像处理 知识图谱 知识网络 kngraph knnet  attilax总结   r1e.xlsx.index.txt
知识图谱res资源包\c、doc r1 home、000r1e、atitit 编程语言 知识图谱 知识网络 知识点 attilax总结 fix r1e v1 r1e.xlsx.index.txt
知识图谱res资源包\c、doc r1 home、00r13、atitit nlp自然语言处理知识图谱体系网络科技树 qc31.xlsx.index.txt
知识图谱res资源包\c、doc r1 home、00r13、atitit nlp自然语言处理知识图谱体系网络科技树 v2 r17.xlsx.index.txt
知识图谱res资源包\doc s228__sql之道资料包__Atitit  补充说明 sql知识图谱与线路图attilax总结补充说明.docx
知识图谱res资源包\doc s228__架构资料包__Atitit 一个完整的体系架构，知识图谱，路线图，科技树，思维导图 结构图.docx
知识图谱res资源包\doc s228__架构资料包__atitit 架构知识图谱知识网络.xlsx
知识图谱res资源包\doc s228__架构资料包__Atitit 知识图谱知识架构体系的构建---定向抓取法.docx
知识图谱res资源包\doc s228__架构资料包__Atitit 知识图谱解决方案：提供完整知识体系架构的搜索与知识结果.docx
知识图谱res资源包\doc s228__架构资料包__新建文件夹__Atitit 一个完整的体系架构，知识图谱，路线图，科技树，思维导图 结构图.docx.txt
知识图谱res资源包\doc s228__架构资料包__新建文件夹__atitit 摄像头与onvif与流媒体 知识图谱网络 科技树 架构体系 ipc stream media knmap techtree v2qc27.xlsx
知识图谱res资源包\doc s228__架构资料包__新建文件夹__Atitit 知识图谱知识架构体系的构建---定向抓取法.docx.txt
知识图谱res资源包\doc s228__架构资料包__新建文件夹__Atitit 知识图谱解决方案：提供完整知识体系架构的搜索与知识结果.docx.txt
知识图谱res资源包\doc s228__研发体系__Atitit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx
知识图谱res资源包\doc s228__研发体系__新建文件夹__Atitit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx.txt
知识图谱res资源包\kg.txt
知识图谱res资源包\r1 doc、doc r1 home、000qc31、atitit zip rar文件名列表提取 知识图谱 科技树.xlsx.index.txt
知识图谱res资源包\r1 doc、doc r1 home、000r19、atitit 架构知识图谱知识网络.xlsx.index.txt
知识图谱res资源包\r1 doc、doc r1 home、000r1b、atitit v8图像处理 知识图谱 知识网络 sysmap  attilax总结 v8 r1d.xlsx.index.txt
知识图谱res资源包\r1 doc、doc r1 home、000r1e、atitit v9图像处理 知识图谱 知识网络 kngraph knnet  attilax总结   r1e.xlsx.index.txt
知识图谱res资源包\r1 doc、doc r1 home、000r1e、atitit 编程语言 知识图谱 知识网络 知识点 attilax总结 fix r1e v1 r1e.xlsx.index.txt
知识图谱res资源包\r1 doc、doc r1 home、00r13、atitit nlp自然语言处理知识图谱体系网络科技树 qc31.xlsx.index.txt
知识图谱res资源包\r1 doc、doc r1 home、00r13、atitit nlp自然语言处理知识图谱体系网络科技树 v2 r17.xlsx.index.txt
知识图谱res资源包\r2 doc、005 r2c、00onvif_ws_wbsvs、Atitit 一个完整的体系架构，知识图谱，路线图，科技树，思维导图 结构图.docx.index.txt
知识图谱res资源包\r2 doc、005 r2c、00onvif、atitit 摄像头与onvif与流媒体 知识图谱网络 科技树 架构体系 ipc stream media knmap techtree v2qc27.xlsx.index.txt
知识图谱res资源包\r7 doc all、r71 doc ntpc、设计文档、atitit v8图像处理 知识图谱 知识网络 sysmap  attilax总结 v8 r1d.xlsx.index.txt
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit  补充说明 sql知识图谱与线路图attilax总结补充说明.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit learn by need 需要的时候学与预先学习知识图谱路线图.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 一个完整的体系架构，知识图谱，路线图，科技树，思维导图 结构图.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 个性化推荐算法；相关知识挖掘 知识图谱挖掘.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 图像处理知识点  知识体系 知识图谱 v2.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 图像处理知识点  知识体系 知识图谱.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 图像处理知识点体系知识图谱 路线图attilax总结 v4 qcb.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 图像处理科技树 知识图谱 补充.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 知识图谱知识架构体系的构建---定向抓取法.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 知识图谱解决方案：提供完整知识体系架构的搜索与知识结果.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx
知识图谱res资源包\s2018 s2 sumdoc onlydoc upby s9__Atitit 项目管理--团队建设知识图谱mybatis知识点体系结构.docx
知识图谱res资源包\s2018 s3 doc all__s2018 s3f doc homepc__外设硬件之道__atitit 摄像头与onvif与流媒体 知识图谱网络 科技树 架构体系 ipc stream media knmap techtree v2qc27.xlsx
知识图谱res资源包\s2018 s3f doc__外设硬件之道__atitit 摄像头与onvif与流媒体 知识图谱网络 科技树 架构体系 ipc stream media knmap techtree v2qc27.xlsx
知识图谱res资源包\sumdoc sb31__Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取 (2).docx
知识图谱res资源包\sumdoc sb31__Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取 (3).docx
知识图谱res资源包\sumdoc sb31__Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx
知识图谱res资源包\sumdoc sb31__Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx (2).txt
知识图谱res资源包\sumdoc sb31__Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx.txt
知识图谱res资源包\sumdoc sb31__titti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx.placehold
知识图谱res资源包\sumdoc sb31__um doc 2005-1014、qa31、0005up know graph、Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx.index (2).txt
知识图谱res资源包\sumdoc sb31__um doc 2005-1014、qa31、0005up know graph、Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx.index.txt
知识图谱res资源包\titit  补充说明 sql知识图谱与线路图attilax总结补充说明.docx.placehold
知识图谱res资源包\titit learn by need 需要的时候学与预先学习知识图谱路线图.docx.placehold
知识图谱res资源包\titit nlp自然语言处理知识图谱体系网络科技树 qc31.xlsx.placehold
知识图谱res资源包\titit sql知识图谱与线路图attilax总结.xlsx.placehold
知识图谱res资源包\titit 一个完整的体系架构，知识图谱，路线图，科技树，思维导图 结构图.docx.placehold
知识图谱res资源包\titit 个性化推荐算法；相关知识挖掘 知识图谱挖掘.docx.placehold
知识图谱res资源包\titit 农历日历的算法以及attilax总结的知识图谱 .docx.placehold
知识图谱res资源包\titit 商业项目常用模块的知识图谱科技树 v3 qc29.xlsx.placehold
知识图谱res资源包\titit 图像处理知识点  知识体系 知识图谱 v2.docx.placehold
知识图谱res资源包\titit 图像处理知识点  知识体系 知识图谱.docx.placehold
知识图谱res资源包\titit 图像处理知识点体系知识图谱 路线图attilax总结 v4 qcb.docx.placehold
知识图谱res资源包\titit 图像处理科技树 知识图谱 补充.docx.placehold
知识图谱res资源包\titit 摄像头与onvif与流媒体 知识图谱网络 科技树 架构体系 ipc stream media knmap techtree v2qc27.xlsx.placehold
知识图谱res资源包\titit 数据处理与数据库技术知识点体系知识图谱attilax大总结 for 研发体系建设 v4 qc7.xlsx.placehold
知识图谱res资源包\titit 知识图谱 与知识体系的分类.docx.placehold
知识图谱res资源包\titit 知识图谱的用途.docx.placehold
知识图谱res资源包\titit 知识图谱知识架构体系的构建---定向抓取法.docx.placehold
知识图谱res资源包\titit 知识图谱解决方案：提供完整知识体系架构的搜索与知识结果.docx.placehold
知识图谱res资源包\titit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx.placehold
知识图谱res资源包\titit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结 v2.xlsx.placehold
知识图谱res资源包\titit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结 v3 qb0.xlsx.placehold
知识图谱res资源包\titit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结.xlsx.placehold
知识图谱res资源包\titit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v10 qb22.xlsx.placehold
知识图谱res资源包\titit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v8 qb20.xlsx.placehold
知识图谱res资源包\titit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v9 qb21.xlsx.placehold
知识图谱res资源包\titit 网络与流媒体方面的知识图谱n科技树attilax总结.xlsx.placehold
知识图谱res资源包\titit 项目管理--团队建设知识图谱mybatis知识点体系结构.docx.placehold
知识图谱res资源包\titti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx.placehold
知识图谱res资源包\titti 知识图谱构建方法attilax 总结.docx.placehold
知识图谱res资源包\ttiti 软件工程知识图谱attilax总结.docx.placehold
知识图谱res资源包\um doc 2005-1014、qa31、0005up know graph、2._知识图谱的数据来源.docx.index.txt
知识图谱res资源包\um doc 2005-1014、qa31、0005up know graph、Atitit 农历日历的算法以及attilax总结的知识图谱 .docx.index.txt
知识图谱res资源包\um doc 2005-1014、qa31、0005up know graph、Atitit 知识图谱的用途.docx.index.txt
知识图谱res资源包\um doc 2005-1014、qa31、0005up know graph、Atitit 知识图谱知识架构体系的构建---定向抓取法.docx.index.txt
知识图谱res资源包\um doc 2005-1014、qa31、0005up know graph、Atitit 知识图谱解决方案：提供完整知识体系架构的搜索与知识结果.docx.index.txt
知识图谱res资源包\um doc 2005-1014、qa31、0005up know graph、Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx.index (2).txt
知识图谱res资源包\um doc 2005-1014、qa31、0005up know graph、Atitti 知识图谱-----人员关系的联系获取-------通过手机通讯录抓取.docx.index.txt
知识图谱res资源包\um doc 2005-1014、qa31、0005up know graph、Atitti 知识图谱构建方法attilax 总结.docx.index.txt
知识图谱res资源包\um doc q2016、qa、000case 4 interview、Atitit 个性化推荐算法；相关知识挖掘 知识图谱挖掘.docx.index.txt
知识图谱res资源包\um doc q2016、qa、000case 4 interview、Atitit 知识图谱知识架构体系的构建---定向抓取法.docx.index.txt
知识图谱res资源包\um doc q2016、qa、000case 4 interview、Atitit 知识图谱解决方案：提供完整知识体系架构的搜索与知识结果.docx.index.txt
知识图谱res资源包\um doc q2016、qa、000case 4 interview、新建文件夹、2._知识图谱的数据来源.docx.index.txt
知识图谱res资源包\um doc q2016、qa、qak、Atitit 知识图谱 与知识体系的分类.docx.index.txt
知识图谱res资源包\um doc q2016、qc5、00 tech tree、Atitit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx.index.txt
知识图谱res资源包\um doc q2016、qc5、00 tech tree、atitit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结 v3 qb0.xlsx.index.txt
知识图谱res资源包\um doc q2016、qc5、0005 qb29、Atitit 图像处理知识点  知识体系 知识图谱 v2.docx.index.txt
知识图谱res资源包\um doc q2016、qc5、005 QB1124、Atitit 图像处理知识点  知识体系 知识图谱.docx.index.txt
知识图谱res资源包\um doc q2016、qc5、atitit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结 v2.xlsx.index.txt
知识图谱res资源包\um doc q2016、qc5、atitit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结.xlsx.index.txt
知识图谱res资源包\um doc q2016、qc5、Atitit 项目管理--团队建设知识图谱mybatis知识点体系结构.docx.index.txt
知识图谱res资源包\um doc q2016、qcb、005 up q1207、Atitit  补充说明 sql知识图谱与线路图attilax总结补充说明.docx.index.txt
知识图谱res资源包\um doc q2016、qcb、005 up q1207、atitit sql知识图谱与线路图attilax总结.xlsx.index.txt
知识图谱res资源包\um doc q2016、qcb、005 up q1207、atitit 数据处理与数据库技术知识点体系知识图谱attilax大总结 for 研发体系建设 v4 qc7.xlsx.index.txt
知识图谱res资源包\um doc q2016、qcb、005 up qc8、Atitit  补充说明 sql知识图谱与线路图attilax总结补充说明.docx.index.txt
知识图谱res资源包\um doc q2016、qcb、005 up qc8、atitit sql知识图谱与线路图attilax总结.xlsx.index.txt
知识图谱res资源包\um doc q2016、qcb、atitit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结 v3 qb0.xlsx.index.txt
知识图谱res资源包\um doc q2016、qd1、005 qc18、Atitit learn by need 需要的时候学与预先学习知识图谱路线图.docx.index.txt
知识图谱res资源包\um doc q2016、qd1、005 qc20、atitit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v9 qb21.xlsx.index.txt
知识图谱res资源包\um doc q2016、qd1、005 qc22、Atitit 图像处理科技树 知识图谱 补充.docx.index.txt
知识图谱res资源包\um doc q2016、qd1、00qc29、atitit nlp自然语言处理知识图谱体系网络科技树 qc31.xlsx.index.txt
知识图谱res资源包\um doc q2016、qd1、00qc29、atitit 商业项目常用模块的知识图谱科技树 v3 qc29.xlsx.index.txt
知识图谱res资源包\um doc q2016、qd31 com、005 qc20、atitit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v8 qb20.xlsx.index.txt
知识图谱res资源包\um doc q2016、qd31 com、005 qcb、Atitit 图像处理知识点体系知识图谱 路线图attilax总结 v4 qcb.docx.index.txt
知识图谱res资源包\um doc q2016、qd31 com、00qc28、atitit 网络与流媒体方面的知识图谱n科技树attilax总结.xlsx.index.txt
知识图谱res资源包\um doc q2016、qd31 com、Atitit 图像处理知识点体系知识图谱 路线图attilax总结 v4 qcb.docx.index.txt
知识图谱res资源包\um doc q2016、qd31 com、atitit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v10 qb22.xlsx.index.txt
知识图谱res资源包\um doc q2016、qd31 com、Attiti 软件工程知识图谱attilax总结.docx.index.txt
知识图谱res资源包\【重磅推荐】34张史上最全IT架构师技术知识图谱 - 51CTO.COM.placeholder
知识图谱res资源包\新建文件夹
知识图谱res资源包\直播技术-知识图谱n科技树attilax搜集.png
知识图谱res资源包\新建文件夹\Atitit  补充说明 sql知识图谱与线路图attilax总结补充说明.docx
知识图谱res资源包\新建文件夹\Atitit learn by need 需要的时候学与预先学习知识图谱路线图.docx
知识图谱res资源包\新建文件夹\atitit nlp自然语言处理知识图谱体系网络科技树 qc31.xlsx
知识图谱res资源包\新建文件夹\atitit nlp自然语言处理知识图谱体系网络科技树 v2 r17.xlsx
知识图谱res资源包\新建文件夹\atitit sql知识图谱与线路图attilax总结.xlsx
知识图谱res资源包\新建文件夹\atitit v8图像处理 知识图谱 知识网络 sysmap  attilax总结 v8 r1d (1).xlsx
知识图谱res资源包\新建文件夹\atitit v8图像处理 知识图谱 知识网络 sysmap  attilax总结 v8 r1d.xlsx
知识图谱res资源包\新建文件夹\atitit v9图像处理 知识图谱 知识网络 kngraph knnet  attilax总结   r1e.xlsx
知识图谱res资源包\新建文件夹\atitit zip rar文件名列表提取 知识图谱 科技树.xlsx
知识图谱res资源包\新建文件夹\Atitit 农历日历的算法以及attilax总结的知识图谱 .docx
知识图谱res资源包\新建文件夹\atitit 商业项目常用模块的知识图谱科技树 v3 qc29.xlsx
知识图谱res资源包\新建文件夹\Atitit 图像处理知识点  知识体系 知识图谱 v2.docx
知识图谱res资源包\新建文件夹\Atitit 图像处理知识点  知识体系 知识图谱.docx
知识图谱res资源包\新建文件夹\Atitit 图像处理知识点体系知识图谱 路线图attilax总结 v4 qcb.docx
知识图谱res资源包\新建文件夹\Atitit 图像处理科技树 知识图谱 补充.docx
知识图谱res资源包\新建文件夹\atitit 摄像头与onvif与流媒体 知识图谱网络 科技树 架构体系 ipc stream media knmap techtree v2qc27.xlsx
知识图谱res资源包\新建文件夹\atitit 数据处理与数据库技术知识点体系知识图谱attilax大总结 for 研发体系建设 v4 qc7.xlsx
知识图谱res资源包\新建文件夹\atitit 架构知识图谱知识网络.xlsx
知识图谱res资源包\新建文件夹\Atitit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx
知识图谱res资源包\新建文件夹\Atitit 研发体系建立 数据存储与数据知识点体系知识图谱attilax 总结.docx.txt
知识图谱res资源包\新建文件夹\atitit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结 v2.xlsx
知识图谱res资源包\新建文件夹\atitit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结 v3 qb0.xlsx
知识图谱res资源包\新建文件夹\atitit 研发体系建设--数据处理 数据库技术知识点体系知识图谱attilax大总结.xlsx
知识图谱res资源包\新建文件夹\atitit 编程语言 知识图谱 知识网络 知识点 attilax总结 fix r1e v1 r1e.xlsx
知识图谱res资源包\新建文件夹\atitit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v10 qb22.xlsx
知识图谱res资源包\新建文件夹\atitit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v8 qb20.xlsx
知识图谱res资源包\新建文件夹\atitit 编程语言知识图谱网络and科技树and路线图prgrm tech tree roadmap v9 qb21.xlsx
知识图谱res资源包\新建文件夹\atitit 网络与流媒体方面的知识图谱n科技树attilax总结.xlsx
知识图谱res资源包\新建文件夹\Atitit 项目管理--团队建设知识图谱mybatis知识点体系结构.docx
知识图谱res资源包\新建文件夹\Attiti 软件工程知识图谱attilax总结.docx


王昊奋：大规模知识图谱技术_zhaoxq_新浪博客.html
(5条消息)肖仰华谈知识图谱：知识将比数据更重要，得知识者得天下 - AI科技大本营 - CSDN博客.html
