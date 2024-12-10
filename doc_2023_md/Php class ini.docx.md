Php class ini



但是php中并没有一个类似java中的静态构造器/静态块的东西，就没有合适的时机对其进行初始化了。

对于共有的成员还有办法解决，例如：
1 class A {
2     static public $child;
3 }
4 A::$child = new B();

对于私有的成员似乎就没有什么干净的方法了，只能这样做：

1 class A {
2     static private $child;
3     static public initialize() {
4         self::$child = new B();
5     }
6 }
7 A::initialize();

