泛型编程（Generic Programming）




泛型 就是参数化类型。动态类型模式了。提升了算法通用性
泛型编程是一种通用的编程范式，通过使用泛型来实现“一次编写，多次使用”的代码。泛型将数据类型与方法实现分离，使得数据类型只是一个参数，不影响方法的实现。这样可以提高代码的复用性和可维护性


可以说泛型编程是一种更加抽象化的编程方式，它关注的是数据类型的通用性，而非具体的数据类型实现。而面向对象编程则是更加具体化的编程方式，它关注的是不同数据类型的具体实现和数据类型之间的关系。

泛型编程（Generic Programming）最初提出时的动机很简单直接：发明一种语言机制，能够帮助实现一个通用的标准容器库。所谓通用的标准容器库，就是要能够做到，比如用一个List类存放所有可能类型的对象这样的事；泛型编程让你编写完全一般化并可重复使用的算法，其效率与针对某特定数据类型而设计的算法相同。泛型即是指具有在多种数据类型上皆可操作的含意，与模板有些相似。STL巨大，而且可以扩充，它包含很多计算机基本算法和数据结构，而且将算法与数据结构完全分离，其中算法是泛型的，不与任何特定数据结构或对象类型系在一起。
泛型编程最初诞生于C++中，由Alexander Stepanov[2]和David Musser[3]创立。目的是为了实现C++的STL（标准模板库）。其语言支持机制就是模板（Templates）。模板的精神其实很简单：参数化类型。换句话说，把一个原本特定于某个类型的算法或类当中的类型信息抽掉，抽出来做成模板参数T。比如qsort泛化之后就变成了：

。另外，一提到泛型，相信大家用到最多的就是在集合中，其实，在实际的编程过程中，自己可以使用泛型去简化开发，且能很好的保证代码质量


泛型的用途：：
主要简化代码编写，方便ide代码检查
使用场景：：编写 比较基础框架类库或者基础代码



是一种以通用的方式编写代码以适应不同类型的数据的编程方法。泛型编程的目的是编写可以在不考虑具体数据类型的情况下工作的代码，从而提高代码的复用性和性能。泛型编程通过使用类型参数（或称为模板参数）来实现通用性。类型参数可以在代码中用于定义变量、函数或类，从而使它们能够适用于多种不同的数据类型。通过泛型编程，可以实现在编译时对类型进行检查，提供更好的类型安全性，并避免代码中的类型转换。


以Type为中心，GP以Concept为中心，而Concept完全独立于Type；OO的type是显式定义的，type之间的关系也是显式定义的，


·  以GP写就的算法，自动满足最小接口原则，无需为其参数定义形式化的类型；在OO中，这种形式化的Type具有的操作往往不是所有用到该Type的算法都会用到的
·  ·  OOP支持二进制组件形式的复用，GP支持源码层级的复用；与二进制码相比较，源码天生具有更多信息和更高级别，所以泛型编程支持更丰富的构件，但其代价是较弱的执行期动态性

提高代码的重用性   提升重用性 类型无关
如果只是重用性的化，object也可以实现
类型安全 增加ide检查提示
“泛型编程的中心思想通用的算法
是对具体的、高效的算法进行抽象，
以获得通用的算法，然后这些算法可以与不同的数据表示法结合起来，产生各种各样有用的软件”。说白了就是将算法与类型解耦，实现算法更广泛的复用。


增强代码的可读性，让抽象变得更加具体和实用。基于泛型的程序，由于传入的参数不同，程序会实现不同的功能。这也被叫做一种多态现象，叫做参数化多态（Parametric Polymorphism）。


在实际的程序设计中，泛型编程和面向对象编程可以同时使用。例如，Java中的泛型就是基于面向对象编程思想的，通过使用泛型可以提高程序的复用性和可读性。另外，C++中也有泛型编程的支持，通过使用模板的方式实现泛型编程，可以提高代码的可重用性和可维护性。
理想情况下，算法应是和数据结构以及类型无关的，各种特殊的数据类型理应做好自己分内的工作。算法只关心一个标准的实现。而对于泛型的抽象，我们需要回答的问题是，如果我们的数据类型符合通用算法，那么对数据类型的最小需求是什么？

泛型编程需要解决如下几个泛型编程的问题：
存储的泛型
算法的泛型；类型的泛型；
数据结构（数据容器）的泛型
在 C++ 的泛型版本中，我们可以看到：

使用typename T抽象了数据结构中存储数据的类型。


使用typename Iter，这是不同的数据结构需要自己实现的“迭代器”，这样也就抽象掉了不同类型的数据结构。


然后，我们对数据容器的遍历使用了Iter中的++方法，这是数据容器需要重载的操作符，这样通过操作符重载也就泛型掉了遍历。


在函数的入参上使用了

上面的代码是我写的一个迭代器（这个迭代器在语义上是没有问题的），我没有把所有的代码列出来，而把它的一些基本思路列了出来。这里我说明一下几个关键点。

首先，一个迭代器需要和一个容器在一起，因为里面是对这个容器的具体的代码实现。


它需要重载一些操作符，比如：取值操作*、成员操作->、比较操作==和!=，还有遍历操作++，等等。


然后，还要typedef一些类型，比如value_type，告诉我们容器内的数据的实际类型是什么样子。


还有一些，如begin()和end()的基本操作。



这就是整个 STL 的泛型方法，其中包括：
泛型的数据容器；
泛型数据容器的迭代器；
然后泛型的算法就很容易写了。

泛型实现模式
通俗理解，占位符号 模板机制
  定义：：： 类型参数（专业说法）  ，，
简单理解  占位符 代替object、
。模板的精神其实很简单：参数化类型。换句话说，把一个原本特定于某个类型的算法或类当中的类型信息抽掉，抽出来做成模板参数T。

每个类必须实现某个xx方法，方便进入算法list调用使用

Object superclass与泛型
类型通配符

在Java SE 1.5之前，没有泛型的情况的下，通过对类型Object的引用来实现参数的“任意化”，“任意化”带来的缺点是要做显式的强制类型转换，而这种转换是要求开发者对实际参数类型可以预知的情况下进行的。对于强制类型转换错误的情况，编译器可能不提示错误，在运行的时候才出现异常，这是一个安全隐患。
泛型的好处是在编译的时候检查类型安全，并且所有的强制转换都是自动和隐式的，提高代码的重用率




泛型相关技术
Tmplt 模板技术 提供模板用来泛型绑定
就到了函数式编程。
函数式编程里面，我们可以用很多的像 reduce 这样的函数来完成更多的像 STL 里面的count_if()这样的有具体意义的函数。关
Reduce 函数
我们来看看如何使用 reduce 和其它函数完成一个更为复杂的功能。


How使用怎么使用。。。

泛型有三种使用方式，分别为：泛型类、泛型接口、
泛型方法

4.5 泛型通配符 ？ 问号
我们知道Ingeter是Number的一个子类，同时在特性章节中我们也验证过Generic<Ingeter>与Generic<Number>实际上是相同的一种基本类型
可以解决当具体类型不确定的时候，这个通配符就是 ?  ；当操作类型时，不需要使用类型的具体功能时，只使用Object类中的功能。那么可以用 ? 通配符来表未知类型。

类型通配符
1、类型通配符一般是使用?代替具体的类型参数。例如 List<?> 在逻辑上是List<String>>,List<Integer> 等所有List<具体类型实参>的父类。


泛型的数据存储 使用json
Lowdb  mgdb









