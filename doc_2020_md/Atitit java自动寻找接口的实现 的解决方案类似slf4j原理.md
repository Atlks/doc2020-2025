Atitit java自动寻找接口的实现 的解决方案类似slf4j原理


　简单的说下它的原理，就是通过工厂类，提供一个用户的接口！用户可以通过这个外观接口，直接使用API实现日志的记录。而后面的具体实现由Slf4j来寻找加载.寻找的过程，就是通过类加载加载那个叫org/slf4j/impl/StaticLoggerBinder.class的文件，只要实现了这个文件的日志实现系统，都可以作为一种实现方式。如果找到很多种方式，那么就寻找一种默认的方式。
　　这就是日志接口的工作方式，简单高效，关键是完全解耦！不需要日志实现部分提供任何的修改配置，只需要符合接口的标准就可以加载进来。



日志那点事儿——slf4j源码剖析 - xingoo - 博客园.html
