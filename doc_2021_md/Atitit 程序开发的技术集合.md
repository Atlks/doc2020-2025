Atitit 程序开发的技术集合

桌面环境
在 11 发布时，JavaFX 也发布了 11 的 GA 版本。JavaFX 本身并不新奇，但自 Java9 模块化后，JavaFX 得益于 jlink 的能力，能够将 JavaFX 封装为独立的 GUI 应用，不要求安装JDK 。这使得在桌面应用开发的场景，除了 Electron、Mono、QT 等跨平台开发框架，Java 也能作为其中的一项选择了。在 Swing 时代，Java的桌面应用开发体验也不差（曾经做过的小游戏 wenerme/GTetris），但由于累赘的 JDK （大约 150m）使得开发一个小应用变得不切实际

JLink 可以将项目依赖的模块加上基础VM来生成一个新的 JDK，应用的体积能够大大减小，如果还能再配合 progard，那体积还能再缩小一圈。

# 生成的 JDK 大约 50m - 对此已经非常满意了，Electron 一般都是 100m 左右
du -s jdk/
Atitit java 原生 客户端 native desktop桌面 javafx 浏览器环境


Ui 常见的h5 或原生代码法

业务逻辑php js go java python或其他

数据库 sql
