Oop prblm


会使代码复杂化，难以理解而且难以测试。
然而，随着时间的推进，人们开始意识到严格的面向对象方法会带来许多问题。这些问题往往会使代码复杂化，难以理解而且难以测试。
事实证明，OOP在某些问题领域确实比其他方法更出色。例如，OOP仍然是构建用户界面（窗口和按钮）的最自然的方式。但是，试图使面向对象适应关系数据库一直以来都简直是一场灾难。
以下是我所观察到的一些问题：



这使得给这些对象写单元测试异常困难。这些复杂的对象在被创建出来之前就需要大量的基础结构。这意味着为了测试一个对象，我必须创建大量的脚手架来满足所有先决条件。
大部分项目90%是中小项目根本不必要oop
或者限制oop的代码规模在10%
“鸭嘴兽”效应
现实世界并不总是能被整洁地划分为具有明确属性定义的类（class）。例如，假设你创建了一个代表动物王国的类层次结构。现在，有爬行动物——冷血，有鳞片，卵生等等。还有哺乳动物——温血，有绒毛，胎生。以及鸟类，两栖动物，无脊椎动物等等
然后鸭嘴兽出现了，它似乎不适合你的任何类别。你该怎么做呢？你是创建一个全新的类别呢，还是重新考虑整个分类方案？这两种方法在工作量和程序复杂性方面都会产生巨大的成本。
（感谢Anselm Hook创造了“鸭嘴兽效应”一词。）
.后来有网友更是将 OOP 称之为是反模块化、反并行的
深层次结构
九个级别的类。太多了。
但情况会变得更糟。
许多高级类被只与少数子类相关的方法和属性“污染”。例如，“Control”类有超过90种方法（method）。它具有设置状态的方法，即使特定的子类是无状态的; 它有添加和删除子元素的方法，即使对control来说子元素没有意义。
这种复杂性的一个重要原因是，该库的作者试图组织组件的不同方面——例如组件是按钮还是滑块，或者它是否有颜色——并通过将它们放入类的不同层次来实现这一点。
但实际上，这些不同方面彼此之间无关。咖啡杯是红色的，和它是由陶瓷制成的，这是两个独立的特性。将红色咖啡杯划入“红色物品”类别，还是将其放入“陶瓷制品”甚至“家居用品”类别中都是同样正确的。任何一个选择都是任意的，因为类别是由人头脑中的反映和社会结构决定的。

我记得我在谷歌工作时，当时我们有一个JavaScript库叫goog.ui，

我们采用的规则之一（以典型的Google风格，以方程式编写）是：
composition > inheritance
复制
用直白的英语解释的话，这说的是：
“更偏向于采用组合的思路——也就是说，能够用更小的构建块来组装组件的功能——而不是继承作为代码重用的手段。”
因此，举个栗子，如果按钮有颜色，你将采用常规的“Button”对象(object)并向其添加“Color”方面(aspect)，作为属性或子对象，而不是创建一个新的“Color Button”类。
作为这项任务的结果，新工具包的类层次结构相对较浅，如果我没记错的话，只有两三个级别。而且更容易理解和使用，也更强大。

最低0
不，面向对象编程（OOP）并没有消亡。但它远没有以前那么流行了。

对象不是真实的
Buckminster Fuller曾经说过：“事物并不存在”。他的意思是，事物之间的区别主要由人的偏见导致。
例如，我坐的沙发是由分子力束缚在一起的原子的集合。然而，这些原子也会受到房间内其他物体的影响——地毯，茶几，甚至是房间内的空气。沙发本身由各种部件组成——织物，木材，金属弹簧等等——它们也受到分子力的约束。那么沙发是一个对象，还是很多对象？也许世上只有一个对象——即我们所在的这个宇宙。
因为人类的视觉和触觉在很大程度上只对表面属性有响应——比如颜色和质感——我们倾向于基于表面现象对世界进行分类。相反，想象一下，如果我们能够直接感知周围物体内的分子组成。我们可能会看到一个“铜”对象，代表着房屋中的所有布线和管道，一个“氮”对象，代表着房间的气体，一个“水”对象，一个“木头”对象，等等。
Fuller的观点是，我们将世界“解析”为离散的“事物”的能力是任意的，这更多地反映了我们的人类心理而不是物理现实。
因为面向对象的继承涉及将事物组织成类，所以它不能很好地模拟现实世界; 但它能很好地模拟人类思考现实世界的方式。


方法（method）也不真实
我记得大约二十年前的一段小插曲，一位软件供应商的技术代表试图向我司的工程人员解释OOP。他试图争辩说，面向对象是一种模拟现实世界的方式，他给出的例子就像上面说的咖啡杯那种。他说杯子可能有个“drink（）”的方法。
我记得的是，我对此有一个非常强烈的反应——我认为他所说的完全是胡说八道。除了它的特定目的之外，一个物理对象可以有许多用途。我可以用咖啡杯作为镇纸或门挡; 这是否意味着它有一个“holdDownPapers（）”或


有时候，如果算法独立于任何对象之外，反而更好

在我最新的编译器中，所有这些内部数据结构都是“傻瓜型”的，意思是说它们所做的只是保存数据而已，没有别的。用于操作和转换对象的所有代码都在这些对象的外部。
这对代码的组织有很大的好处。每个算法都集中在一个地方，而不是分散在一堆源文件中。当我想测试一个特定的编译器操作时，我可以轻松地创建一些示例对象并将其提供给该操作。因此，我的测试写起来更容易了，所以我就能写更多的测试了，从而就能有比以前更好的测试覆盖率了。


函数式编程
在过去十年左右的时间里，人们越来越关注函数式编程（FP）。与OOP一样，函数式编程不仅仅是单纯的一件事物，而是一套整体的风格上的原则。然而，它的要点是，虽然OOP专注于与对象进行交互或通信，但在FP中，重点在于对它们的转换。这里的“转换”，意思是你获取一些对象，将它传递给一个函数，结果是一个全新的对象，代表着对输入内容所做的一些转换。原始对象要么被保留，要么被丢弃，但不会以任何方式被更改或修饰。
在我自己的编程过程中，我更喜欢“混合”方法，在某些地方使用FP技术，而在其他地方使用OOP技术。在解决某些问题上FP确实能大放异彩，但也有另一些问题上OOP是更明智的选择。
