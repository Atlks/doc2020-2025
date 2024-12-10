Atitit log fix   u33


对应关系
LogManager与logger是1对多关系，整个JVM运行时只有一个LogManager，且所有的logger均在LogManager中。
logger与handler是多对多关系，logger在进行日志输出的时候会调用所有的hanlder进行日志的处理。
handler与formatter是一对一关系，一个handler有一个formatter进行日志的格式化处理。
很明显：logger与level是一对一关系，hanlder与level也是一对一关系 。


作者：小布_cvg
链接：https://www.jianshu.com/p/ef810be73e5d
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

