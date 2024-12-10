Atitit mybatis 变量绑定 sql



Druid技巧之使用PrepareStatement时输出完整SQL语句

夫礼者 2018-03-13 17:53:11  9624  收藏 3
分类专栏： druid 文章标签： druid sql PrepareStatement
版权
为了防止SQL注入，我们通过采用PrepareStatement代替Statement。使用Mybatis的情况下就是使用 #{} 来代替 ${} 。
凡事有利必有弊，这样带来了安全性，但随之而来的是调试阶段的检测SQL正确性的繁琐。因为我们需要一个个将？替换为原始的值才能放到诸如plsql里去执行。
本文介绍如何在Druid中粗略解决这个问题。

