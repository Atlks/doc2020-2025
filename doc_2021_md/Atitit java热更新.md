Atitit java热更新


热更新
这样基本上可以实现我们的需求了，但是如果想要实现通过替换class文件来动态修复线上Bug，会发现并没有生效，执行的还是原来的结果，这是因为 Java 的类加载是存在缓存的，代码有删减：
protected Class<?> loadClass(String name, boolean resolve)
        throws ClassNotFoundException
{
    // 先检查缓存是否加载过
    Class<?> c = findLoadedClass(name);
    if (c == null) {
        // 未加载过委托父类加载
        if (parent != null) {
            c = parent.loadClass(name, false);
        } else {
            c = findBootstrapClassOrNull(name);
        }
        // 加载类信息
        if (c == null) {
            c = findClass(name);
        }
    }
    if (resolve) {
        resolveClass(c);
    }
    return c;
}
复制代码有什么办法可以跳过缓存呢？是否可以主动卸载类呢？Java 没有提供对应的API，只能通过自定义类加载器实现。
思路：通过 Map 缓存类的最新修改时间，每次加载的时候检查 class 文件的修改时间是否和缓存一致，不一样则重新加载。

作者：废物点心
链接：https://juejin.cn/post/6844903748389584909
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
