Atitit oracle新特性5 6 7 8 9 10 11 12 18 19 20 attilax总结

:ora 20c
1. 原生的区块链支持 - Native Blockchain Tables
2. 持久化内存存储支持 - Persistent Memory Store
3. SQL的宏支持 - SQL Macro
 4. SQL新特性和函数扩展 - Extensions
5. 自动化的In-Memory 管理 - Self-Managing In-Memory
6. 广泛的机器学习算法和AutoML支持
 9. In-Memory 的 Spatial 和 Text 支持  地理信息 -Spatial 和 全文检索 - Text 组件

针对 Oracle 数据库内置的多模特性，地理信息 -Spatial 和 全文检索 - Text 组件，在 20c 中，通过 In-Memory 的内存特性，获得了进一步的支持。

对于空间数据，Oracle 在内存中为空间列增加空间摘要信息（仅限于内存中，无需外部存储），通过 SIMD 矢量快速过滤、替换 R-Tree 索引等手段，以加速空间数据查询检索，可以将查询速度提升10倍。

20cNF09.jpg

针对全文检索（Text），在内存中将倒排索引添加到每个文本列，同时通过将单词映射到包含单词的文档，以内存替换原来的磁盘索引，从而加速全文检索的性能。通过结合关系数据和文本的混合查询，全文检索可以获得 3倍以上的性能提升。


Oracle Database 19c 的10大新特性早知道	3
 
 
 
4.自动化索引创建和实施	6
 
6.Oracle的混合分区表支持	8
7.在线维护操作增强	9
8.自动的统计信息管理	9
9.自动化的SQL执行计划管理	10
10.SQL功能的增强	1
 Oracle Database 18c 的10大新特性一览	3
 4
4.In-Memory的外部表和InLine外部表支持	5
5.近似查询 - Approximate Query 和 Top-N 近似聚合	6
6.机器学习算法新特性	6
7.多态表支持	7
 只听过8i/9i/10g/11g/12c i 表示internet g 表示grid c 表示cloud
Oracle(甲骨文)。该公司成立于1977年，最初是一家专门开发数据库的公司。Oracle在数据库领域一直处于领先地位。1984年，首先将关系数据库转到了桌面计算机上。然后，
Oracle1  
Oracle5率先推出了分布式数据库、客户/服务器结构等崭新的概念。
Oracle6首创行锁定模式以及对称多处理计算机的支持……
最新的Oracle8主要增加了对象技术，成为关系—对象数据库系统

1984年10月，Oracle(RSI更名为Oracle)发布了第4版产品。这一版增加了读一致性这个重要特性。
1985年，Oracle发布了5.0版。这个版本是Oracle数据库较为稳定的版本。并实现了C/S模式工作。
1986年，Oracle发布了5.1版。该版本开始支持分布式查询。
1988年，Oracle发布了第6版。该版本中引入了行级锁特性，同时还引入了联机热备份功能。
1992年6月，Oracle发布了第7版。该版本增加了包括分布式事务处理功能、用于应用程序开发的新工具及安全性方法等功能。
1997年6月，Oracle第8版发布。Oracle8支持面向对象的开发及新的多媒体应用。
1998年9月，Oracle公司正式发布Oracle 8i。正是因为该版本对Internet的支持，所以，在版本号之后，添加了标识i。
2001年6月，Oracle发布了Oracle 9i。
2003年9月，Oracle发布了Oracle 10g。这一版的最大特性就是加入了网格计算的功能，因此版本号之后的标识使用了字母g，代表Grid--网格。

Ora 13-17 cant find
Oracle 11  12
ORACLE 11G新特性 
1 oracle11G新特性
2 审计
3 1   审计简介
4 其他大部分是管理功能
Oracle 12c 的 12 个新特性
1 2 Improved Defaults 增强了DEFAULT default目前可以直接指代sequence了同时增强了default充当identity的能力
2 Easy Top-N and pagination queries 更易用的Top-N和页码查询
Oracle 10G 新特性简介
eref
atitit.Oracle 9 10 11 12新特性attilax总结 - attilax的专栏 - 博客频道 - CSDN.NET.html
Oracle数据库发展历史 - 采乃 - 博客园.html
atitit.Oracle 9  10 11  12新特性
资料整理——Oracle版本历史（很全面）（Releases and versions of Oracle Database）_预见未来to50的专栏-CSDN博客_oracle历史版本

