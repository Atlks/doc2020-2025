Atitit 深入理解抽象类与接口 attilax总结

1.1. 主要区别接口侧重于动作抽象。。抽象类是属性名词抽象。。	1
1.2. 抽象层次类》》抽象类》》接口	1
1.3. 既然有了接口为什么还要定义抽象类,？？	1
1.4. 其次，抽象中间有不同的抽象层次，抽象类的的极限就是接口	2
1.5. 他们两者之间对抽象概念的支持有很大的相似，有时候甚至可以互换	2
1.6. 抽象类与接口的历史	2
2. 抽象类	2
3. 二、接口	2
3.1. 抽象层次不同。抽象类是对类抽象，而接口是对行为的抽象。	3
3.2. 2设计层次	3
3.3. 抽象类所体现的是一种继承关系，要想使得继承关系合理，父类和派生类之间必须存在"is-a" 关系，即父类和派生类在概念本质上应该是相同的。	4
3.4. 抽象类往往都是通过重构而来的！但是接口就不同， 们要做的就是事前定义好飞的行为接口。	5

主要区别接口侧重于动作抽象。。抽象类是属性名词抽象。。
抽象层次类》》抽象类》》接口

既然有了接口为什么还要定义抽象类,？？
俩者给你不同。。接口侧重于动作抽象。。抽象类是属性名词抽象。。

比如鸟类，一个bird  基类。。是个抽象类。。

鸡，则是bird的子类。。


那如何定义fly（）飞这个方法呢？？很明显不能定义到抽象类里面去，因位不是所有的鸟都会飞。所以只能定义到接口里面去。。

其次，抽象中间有不同的抽象层次，抽象类的的极限就是接口

他们两者之间对抽象概念的支持有很大的相似，有时候甚至可以互换
抽象类与接口的历史

抽象类
       我们都知道在面向对象的领域一切都是对象，同时所有的对象都是通过类来描述的，但是并不是所有的类都是来描述对象的。如果一个类没有足够的信息来描述一个具体的对象，而需要其他具体的类来支撑它，那么这样的类我们称它为抽象类。比如new Animal()，我们都知道这个是产生一个动物Animal对象，但是这个Animal具体长成什么样子我们并不知道，它没有一个具体动物的概念，所以他就是一个抽象类，需要一个具体的动物，如狗、猫来对它进行特定的描述，我们才知道它长成啥样。
二、接口
      接口是一种比抽象类更加抽象的“类”。这里给“类”加引号是我找不到更好的词来表示，但是我们要明确一点就是，接口本身就不是类，从我们不能实例化一个接口就可以看出。如new Runnable();肯定是错误的，我们只能new它的实现类。



抽象层次不同。抽象类是对类抽象，而接口是对行为的抽象。
抽象类是对整个类整体进行抽象，包括属性、行为，但是接口却是对类局部（行为）进行抽象。

2设计层次
      上面只是从语法层次和编程角度来区分它们之间的关系，这些都是低层次的，要真正使用好抽象类和接口，我们就必须要从较高层次来区分了。只有从设计理念的角度才能看出它们的本质所在。一般来说他们存在如下三个不同点：
      1、 抽象层次不同。抽象类是对类抽象，而接口是对行为的抽象。抽象类是对整个类整体进行抽象，包括属性、行为，但是接口却是对类局部（行为）进行抽象。
      2、 跨域不同。抽象类所跨域的是具有相似特点的类，而接口却可以跨域不同的类。我们知道抽象类是从子类中发现公共部分，然后泛化成抽象类，子类继承该父类即可，但是接口不同。实现它的子类可以不存在任何关系，共同之处

、 设计层次不同。对于抽象类而言，它是自下而上来设计的，我们要先知道子类才能抽象出父类，而接口则不同，它根本就不需要知道子类的存在，只需要定义一个规则即可，至于什么子类、什么时候怎么实现它一概不知。比如我们只有一个猫类在这里，如果你这是就抽象成一个动物类，是不是设计有点儿过度？我们起码要有两个动物类，猫、狗在这里，我们在抽象他们的共同点形成动物抽象类吧！所以说抽象类往往都是通过重构而来的！但是接口就不同，比如说飞，我们根本就不知道会有什么东西来实现这个飞接口，怎么实现也不得而知，我们要做的就是事前定义好飞的行为接口。所以说抽象类是自底向上抽象而来的，接口是自顶向下设计出来的。


抽象类所体现的是一种继承关系，要想使得继承关系合理，父类和派生类之间必须存在"is-a" 关系，即父类和派生类在概念本质上应该是相同的。
对于接口则不然，并不要求接口的实现者和接口定义在概念本质上是一致的， 仅仅是实现了接口定义的契约而已。


抽象类往往都是通过重构而来的！但是接口就不同， 们要做的就是事前定义好飞的行为接口。

java提高篇（四）-----抽象类与接口 - chenssy的博客 - 博客频道 - CSDN.NET.htm



作者:: 绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher 王中之王King of Kings 虔诚者Pious 宗教信仰捍卫者 Defender of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak
简称：： Emir Attilax Akbar 埃米尔 阿提拉克斯 阿克巴
全名：：Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 
埃米尔 阿提拉克斯 阿克巴 本 马哈茂德 本 阿提拉 本 所罗门 本亚当  阿尔 拉帕努伊   
常用名：atl（ail），   EMAIL:1466519819@qq.com


头衔：uke总部o2o负责人，全球网格化项目创始人，
uke宗教与文化融合事务部部长， uke宗教改革委员会副主席
，Uke部落首席大酋长，
uke制度与重大会议委员会委员长，uke保安部首席大队长,uke制度检查委员会副会长，
奶牛科技cto ，uke 首席cto 
uke波利尼西亚区大区连锁负责人，克尔格伦群岛区连锁负责人，莱恩群岛区连锁负责人，uke汤加王国区域负责人。布维岛和南乔治亚和南桑威奇群岛大区连锁负责人 
 Uke软件标准化协会理事长理事长 uke终身教育学校副校长 
Uke 数据库与存储标准化协会副会长 uke出版社编辑总编
Uke医院方面的创始人

转载请注明来源：attilax的专栏   http://blog.csdn.net/attilax
--Atiend

