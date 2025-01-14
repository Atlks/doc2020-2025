自定义渲染html 算法  布局引擎


如上所示，api 的核心在于创建节点的三个参数：
tagName 节点名，这里我们支持基本的元素，像view,image,text,scroll-view等，另外还支持自定义标签，通过全局componentapi 来注册一个新的组件，利于扩展。

options，即标签的参数，支持styles,attrs,on，分别为样式、_属性_、_事件_
children，即子节点，同时也可以是文字。
我们期望执行以上 api 后可以在 canvas 中渲染出文字，并且点击后可以响应相应事件。
渲染将按以下流程执行，后面也会按照这个顺序进行讲解：  dom节点。。构建，尺寸计算， 位置计算。。


布局处理
在上一步预处理过后，我们就得到了一个带有完整样式的节点树，接下来需要计算布局，计算布局分为尺寸和位置的计算，这里需要注意的是，流程里为什么要先计算尺寸呢？仔细思考一下，如果我们先计算位置，像文字，图片这种之后的节点，是需要在上一个尺寸位置计算完毕再去参考计算。所以这一步是所有节点原地计算尺寸完毕后，再计算所有节点的位置。
计算尺寸
更专业一点的说法应该是计算盒模型，说到盒模型大家应该是耳熟能详了，基础面试几乎必问的。
对于一个节点，他的尺寸可以简化为几种情况：
参考父节点，如width:50%。
设置了具体值，如width:100px。
参考子节点，如width:fit-content，另外像image text节点也是由内容决定尺寸。
梳理好这几种模式之后就可以开始遍历计算了，对于一个树我们有多种遍历模式。
这里我们对上面几种情况分别做考虑：
因为是参考父节点所以需要从父到子遍历。
没有遍历顺序要求。
父节点需要等所有子节点计算完成后再进行计算，因此需要广度优先遍历，并且是从子到父。
这里出现了一个问题
代码部分就是遍历在文档流中的直接子节点来累加高度以及宽度，另外处理上比较麻烦的是对于一行会有多个节点的情况，比如inline-block和flex，这里增加了Line对象来辅助管理，在Line实例中会对当前行内的对象



计算位置
计算完尺寸后就可以计算位置了，这里遍历方式需要从父到子进行广度优先遍历，对于一个元素来说，只要确定了父元素以及上一个元素的位置，就可以确定自身的位置。
这一步只需要考虑根据父节点已经上一个节点的位置来确认自身的位置，如果不在文档流中则根据最近的参考节点进行定位。



渲染器
对于绘制单个节点来说分为以下几个步骤：
绘制阴影,因为阴影是在外面的，所以需要在裁剪之前绘制
绘制裁剪以及边框
绘制背景
绘制子节点以及内容，如 Text 和 Image



对了！每个图形的模型都保存了，那是不是可以对这些模型进行修改以及交互呢，首先定一个小目标，实现事件系统。
事件处理器
canvas 中的图形并不能像 dom 元素那样响应事件，因此需要对 dom 事件进行代理，判断在 canvas 上发生事件的位置，再分发到对应的 canvas 图形节点。
如果按照常规的事件总线设计思路，我们只需要将不同的事件保存在不同的List结构中，在触发的时候遍历判断点是否在节点区域，但是这种方案肯定不行，究其原因还是性能问题。
在浏览器中，事件的触发分为捕获与冒泡，也就是说要按照节点的层级从顶至下先执行捕获，触及到最深的节点后，再以相反的顺序执行冒泡过程，List结构无法满足，遍历这个数据结构的时间复杂度会很高，体现到用户体验上就是操作有延迟。
经过一阵的头脑风暴后想到事件其实也可以保存在树结构中，将有事件监听的节点抽离出来组成一个新的树，可以称之为“事件树”，而不是保存在原节点树上。



另外一个重点就是判定事件点是否在元素内，对于这个问题，已经有了许多成熟的算法，如射线法：
时间复杂度：O(n) 适用范围：任意多边形
算法思想：
以被测点 Q 为端点，向任意方向作射线（一般水平向右作射线），统计该射线与多边形的交点数。如果为奇数，Q 在多边形内；如果为偶数，Q 在多边形外。

