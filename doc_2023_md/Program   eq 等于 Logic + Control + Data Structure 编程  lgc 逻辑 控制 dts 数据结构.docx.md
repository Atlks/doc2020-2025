Program   eq 等于 Logic + Control + Data Structure 编程  lgc 逻辑 控制 dts 数据结构



1976年算法 + 数据结构 = 程序

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:42 am]
1976年，瑞士计算机科学家，Algol W，Modula，Oberon 和 Pascal 语言的设计师 Niklaus Emil Wirth写了一本非常经典的书《Algorithms + Data Structures = Programs》，即算法 + 数据结构 = 程序

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:42 am]
Programs》，即算法 + 数据结构 = 程序。

这本书主要写了算法和数据结构的关系，对计算机科学产生了深远的影响。同时这本书也阐明了编程语言的两个方面——数据和对数据的操作。

这本书的第一章中，作者基于Pascal语言阐述了他对结构的理解，并且把结构分为了三个层次，分别为标量数据，基本数据结构和高级数据结构。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:43 am]
Structures = Programs》 一书中，只是提到了数组和结构体这两种基本数据结构，而其书中提出，数组和结构体是每一门高级语言都应该提供的特性，是语言的基础设施。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:43 am]
结构体/对象/类

结构体在不同的语言中称呼可能有所不同，比如C语言，GoLang中我们称之为结构体，在Java中我们称之为类，而在JavaScript中称作对象，它们在逻辑上其实大体是等价的。结构体中存在成员，每个成员都有自己的名称，我们可以通过结构体成员的名称对结构体中的成员进行随机访问。在很多的实现中，结构体也是使用一段连续的内存进行存储的。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:44 am]
我们通常使用指针把结构中的所有元素链接到一起的手段来实现一个链表，常见的高级数据结构有链表、哈希表、树、图等等。到了高级数据结构这个层面，我们已经开始涉及到数据结构中的逻

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:46 am]
他说算那个程序，就是算法加数据。还有一种说法就是逻辑加控制。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:47 am]
逻辑最小就最小操作。。在这里数据和操作是合在一块儿的。，操作流程控制就是控制，就是那个业务流程控制，选择结构，循环结构。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:48 am]
逻辑加控制其实也就是算法。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:48 am]
程序就可以拆分为逻辑加控制加数据。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:50 am]
算法=逻辑+控制（左耳朵耗子：编程的本质是什么？） - zzfx
后来Robert Kowalski进一步提出：算法=逻辑+控制。
其中逻辑是算法的核心，控制主要用于改进算法的效率。在逻辑式编程

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:52 am]
。绝大多数科学计算领域对可靠性这个东西完全不关心，用户输入了奇怪的东西我们通常会要求用户按规矩输入，而不是在程序里面处理各种莫名其妙的情况。比如说一个把

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:55 am]
别跟我提什么API的安全性、什么栈溢出攻击、什么后人的维护需求，我很清楚不存在这种需求）

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:57 am]
算法=逻辑+控制（左耳朵耗子：编程的本质是什么？）
大家应该都听说过等式‘算法+数据结构=程序’吧？这是Pascal设计者Niklaus Wirth的一本著作的书名，它刻画了过程式尤其是结构化编程的思想。后来Robert Kowalski进一步提出：算法=逻辑+控制。其中逻辑是算法的核心，控制主要用于改进算法的效率。在逻辑式编程中，程序员只需表达逻辑，而控制交给编程语言的解释器或编译器去管理

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:58 am]

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 6:00 am]
1979 年，英国逻辑学家和计算机科学家 Robert Kowalski 发表论文 Algorithm = Logic + Control，并且主要开发“逻辑编程”相关的工作。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 6:00 am]
任何算法都会有两个部分， 一个是 Logic 部分，这是用来解决实际问题的。另一个是 Control 部分，这是用来决定用什么策略来解决问题。Logic 部分是真正意义上的解决问题的算法，而 Control 部分只是影响解决这个问题的效率。程序运行的效率问题和程序的逻辑其实是没有关系的。我们认为，如果将 Logic 和 Control 部分有效地分开，那么代码就会变得更容易改进和维护。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 6:01 am]
编程的本质
两位老先生的两个表达式：

Programs = Algorithms + Data Structures
Algorithm = Logic + Control
第一个表达式倾向于数据结构和算法，它是想把这两个拆分，早期都在走这条路。他们认为，如果数据结构设计得好，算法也会变得简单，而且一个好的通用的算法应该可以用在不同的数据结构上。

第二个表达式则想表达，数据结构不复杂，复杂的是算法，也就是我们的业务逻辑是复杂的。我们的算法由两个逻辑组成，一个是真正的业务逻辑，另外一种是控制逻辑。程序中有两种代码，一种是真正的业务逻辑代码，另一种代码是控制我们程序的代码，叫控制代码，这根本不是

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 6:01 am]
总之，通过这两个表达式，我们可以得出：

Program = Logic + Control + Data Structure

 

如果你再仔细地结合我们之前讲的各式各样的编程范式来思考上述这些概念的话，你是否会觉得，所有的语言或编程范式都在解决上面的这些问题。也就下面的这几个事。

Control 是可以标准化的。
遍历数据、查找数据、多线程、并发、异步等
，都是可以标准化的。
上述三点，就是编程范式的本质。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 6:02 am]
遍历循环  map reds flt，， 分支结构都可以标准化

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 6:02 am]
db crud。。并发 异步 都可以标准化
Splt algo nn ctrlk 控制

算法就是具体逻辑。。。具体流程控制交给dsl编译器

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:58 am]
逻辑表达 复制结构  映射表模式。。

十 jarkas 大鱼 刘洋 汤姆, [07/10/2023 5:59 am]
分支结构。。循环结构呢。还是oo模式。。具体底层使用啥具体技术编译器自己实习。可能是jmp实现，可能是结构化线。可能是各种命令模式实现。挥着 fp实现

