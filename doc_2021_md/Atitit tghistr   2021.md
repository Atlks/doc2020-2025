Atitit tghistr   2021.1---2021.5.1


大 鱼, [30.12.20 23:46]
我得方向  巡回支援  回忆录
美國卸任總統常見的職業「選項」是巡迴演講，動筆寫回憶錄，著手總統圖書館的計劃等，有的卸任總統從事人道工作，有的拿起畫筆畫畫

批量方向  性能  同机

十十tom dom atlx akbar al rapanui十, [02.01.21 11:49]
希望的目标，简化业务逻辑，现在业务逻辑为了解决性能问题绕来绕去，业务复杂性大增
面向未来与通用化，其他未来业务调整也可使用

十十tom dom atlx akbar al rapanui十, [02.01.21 22:10]
#attagl  #atcwd #attime
past now future，yesterday today tomorrow, before after/then
#attagl #atcwd
nakaraan ngayon hinaharap, kahapon ngayon bukas, bago pagkatapos
Nung Nakapag when  able

十十tom dom atlx akbar al rapanui十, [03.01.21 01:03]
出租。   如果您想要个人舒适的住房，请在Airbnb上寻找房间，公寓或房屋。大量的房屋选择。在北京租一间公寓每天的费用为30-50美元，在深圳为27美元。一个月内，您可以以600-1500美元的价格租用Airbnb公寓（客房-500美元） -900）。价格取决于房屋的城市，地区和条件。例如，在度假区海滩附近的深圳，一个很好的公寓以600美元的价格租用。长期租金有折扣。

十十tom dom atlx akbar al rapanui十, [03.01.21 01:18]
我在计算机和iPhone上都使用ExpressVPN，并在整个旅途中都拥有互联网！

十十tom dom atlx akbar al rapanui十, [03.01.21 01:30]
不才，来菲律宾快2个月了，在7月份的时候正式交往了一个菲律宾女朋友，从Facebook上找的，当时她在我的帖子中留言，后面经过一段时间段聊天，在7月份确定见面了，她在安吉利斯坐大巴2个多小时过来见面的，来之前说好，我包路费，她先垫着，当时见面有点尴尬，是约在我公寓楼下，在下雨，她还背着一个背包，说今晚不回去了，太远了，能不能借宿一晚，我说没有问题，因为我也是自己一个人租，睡一晚没事，然后先带着他放好行李

十十tom dom atlx akbar al rapanui十, [03.01.21 01:30]
泡妞攻略

十十tom dom atlx akbar al rapanui十, [04.01.21 01:10]
systems."——维基百科

在计算机领域，WAL（Write-ahead logging，预写式日志）是数据库系统提供原子性和持久化的一系列技术。

在使用WAL的系统中，所有的修改都先被写入到日志中，然后再被应用到系统状态中。通常包含redo和undo两部分信息。

为什么需要使用WAL，然后包含redo和undo信息呢？举个例子，如果一个系统直接将变更应用到系统状态中，那么在机器掉电重启之后系统需要知道操作是成功了，还是只有部分成功或者是失败了（为了恢复状态）。如果使用了WAL，那么在重启之后系统可以通过比较日

十十tom dom atlx akbar al rapanui十, [04.01.21 01:15]
引言
Write Ahead Logging，简称WAL，也被翻译成预写式日志，是数据库技术中实现事务日志(Transaction Journal)的一种标准方法，可以实现单机事务的原子性，同时可以提高数据库的写入效率。

思考如下场景，如何确保原子性：写操作修改数据库中a和b的值，二者是一个事务，需要把a和b的最新值持久化到磁盘，假如保存完a的值，系统宕机了，重新启动后，a的值已经写入，但b待写入的值已经丢失，如何发现事务没有完成呢？

十十tom dom atlx akbar al rapanui十, [04.01.21 01:16]
我们看WAL怎么解决宕机和恢复的问题：

写WAL前宕机了，重启后，数据处于事务未执行的状态。
写WAL时宕机了，重启后，可以检查到WAL数据不正确，回滚当事务前的状态。
写WAL后宕机了，重启后，把WAL中记录的操作，应用到数据库文件中，得到事务执行后的状态。
如此，保证了数据的恢复和事务的原子性

十十tom dom atlx akbar al rapanui十, [04.01.21 01:17]
上面提到的都是写操作，看一下使用WAL时的读操作。WAL中可能包含了未写入到数据库文件中的最新值，如果读最新值就需要从WAL中读取，如果WAL中未读到，从数据库读到的就是最新的数据。

十十tom dom atlx akbar al rapanui十, [04.01.21 01:18]
证事务一致性
并发读写，比如SQLite中，读写、读读都是可以并行的，比如读时需要找到WAL某个值最后写入的位置，就可以从该位置读数据，而写操作是在WAL文件后Append，二者并行。但写写不能并行，因为2次写操作都要向WAL文件Append数据，无法同时进行。
WAL文件中记录了数据的历史版本，因此可以读取历史版本的值，甚至把状态回滚到某个历史版本

十十tom dom atlx akbar al rapanui十, [04.01.21 01:19]
Rollback Journal 的原理是，在修改数据库文件中数据之前，先将修改所在分页中的数据备份在另外一个地方，然后才将修改写入到数据库文件中；如果事务失败，则将备份数据拷贝回来，撤销修改；如果事务成功，则删除备份数据提交修改。2019年10月13日
www.jianshu.com › ...
SQLite 数据库WAL 工作模式原理简介- 简书

十十tom dom atlx akbar al rapanui十, [04.01.21 01:20]
缺点
SQLite提到了WAL的几项缺点：

WAL需要VFS的支持。
所有使用数据库的进程必须在同一个机器上，以为WAL是单机的。
多读少写的场景WAL比rollback-journal类型要慢1%~2%

十十tom dom atlx akbar al rapanui十, [04.01.21 01:21]
的能力，也就是本文标题所讲的 crash-safe。即在 InnoDB 存储引擎中，事务提交过程中任何阶段，MySQL突然奔溃，重启后都能保证事务的完整性，已提交的数据不会丢失，未提交完整的数据会自动进行回滚。这个能力依赖的就是redo log和unod log两个日志。

十十tom dom atlx akbar al rapanui十, [04.01.21 01:24]
如果是主从模式下，binlog是必须的，因为从库的数据同步依赖的就是binlog；

如果是单机模式，并且不考虑数据库基于时间点的还原，binlog就不是必须，因为有redo log就可以保证crash-safe能力了；但如果万一需要回滚到某个时间点的状态，这时候就无能为力，所以建议binlog还是一直开启

十十tom dom atlx akbar al rapanui十, [04.01.21 09:08]
并且是最好的。当然，有一些头条新闻，例如普吉岛的Patong和菲律宾的世界三大最佳岛屿（长滩岛，宿雾和巴拉望岛），它们始终是制胜法宝。但是，如果您想与众不同，这里还有另外三个海滩，可为您带来更加独特的度假体

大 鱼, [10.01.21 15:59]
查询指定表中的分区数据情况
SELECT table_name,partition_name,partition_description,table_rows FROM
information_schema.`PARTITIONS`  WHERE table_name = 'customer_login_log';

大 鱼, [10.01.21 16:19]
涉及到例如SUM()和COUNT()这样聚合函数的查询，可以很容易地进行并行处理。这种查询的一个简单例子如 “SELECT salesperson_id, COUNT (orders) as order_total FROM sales GROUP BY salesperson_id；”。通过“并行”，这意味着该查询可以在每个分区上同时进行，最终结果只需通过总计所有分区得到的结果。
通过跨多个磁盘来分散数据查询，来获得更大的查询吞吐量。

作者：道无虚
链接：https://www.jianshu.com/p/1cdd3e3c5b3c
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

大 鱼, [10.01.21 19:17]
SELECT table_name,partition_name,partition_description,table_rows FROM
information_schema.`PARTITIONS`  WHERE table_name = 'aaa_test_pt0107';


3.2 查看表是不是分区表
show table status like '%aaa_test_pt0107%';


2.3.3 表分区使用信息
explain partitions select * from aaa_test_pt0107;

 select count(*) from archive_log_user_coin_20210107;

十十tom dom atlx akbar al rapanui十, [12.01.21 09:57]
五大好。。那个房子的事情你看这样好不好。。大家发动下朋友认识的人，让他们帮忙收购了把它，他们离得近容易办事情啊，费用方面就七万处理了得了。。他们拿过去清理下收拾下转手还是可以赚个翻倍的。我是没精力维护啊

十十tom dom atlx akbar al rapanui十, [20.01.21 00:56]
现在让我们了解事实。根据美国国务院的资料，语言水平分为五个等级。初级熟练程度是指满足日常旅行需求的能力，以及精通大多数个人和地名，路牌，商店名称和号码的知识。这种熟练水平将满足前往中国和台湾的基本旅行需求。

对于商务人士来说，第三级-最低专业水平-意味着您能够以足够的结构准确性和良好的词汇量说该语言。另外，您还可以阅读标准报纸，例行信件和报告。借助全面的专业技能（第四级），您可以在与您的工作需求相关的所有级别上流畅，准确地进行口语和阅读。

最高，第五级别是母语或双语能力，表示您的阅读和听说能力与受过良好教育的母语者相同

大 鱼, [20.01.21 13:57]
NO  ID  外号
1  16716  核桃
2  16723  大鱼
3  16718  MK
4  16717  阿发
5  16719  阿灿
6  16722  学友
7  16729  摩根
8  16721  茅台
9  16725  小绒

大 鱼, [23.01.21 19:20]
undo log的作用
undo是一种逻辑日志，有两个作用：

用于事务的回滚
MVCC
关于MVCC(多版本并发控制)的内容这里就不多说了，本文重点关注undo log用于事务的回滚。

undo日志，只将数据库逻辑地恢复到原来的样子，在回滚的时候，它实际上是做的相反的工作，比如一条INSERT ，对应一条 DELETE，对于每个UPDATE,对应一条相反的 UPDATE,将修改前的行放回去。undo日志用于事务的回滚操作进而保障了事务的原子性。

undo log的写入时机
DML操作修改聚簇索引前，记录undo日志

大 鱼, [23.01.21 19:21]
undo的类型
在InnoDB存储引擎中，undo log分为：

insert undo log
update undo log
insert undo log是指在insert 操作中产生的undo log，因为insert操作的记录，只对事务本身可见，对其他事务不可见。故该undo log可以在事务提交后直接删除，不需要进行purge操作。

而update undo log记录的是对delete 和update操作产生的undo log，该undo log可能需要提供MVCC机制，因此不能再事务提交时就进行删除。提交时放入undo log链表，等待purge线程进行最后的删除

大 鱼, [23.01.21 19:22]
undo log 是否是redo log的逆过程？
undo log 是否是redo log的逆过程？其实从前文就可以得出答案了，undo log是逻辑日志，对事务回滚时，只是将数据库逻辑地恢复到原来的样子，而redo log是物理日志，记录的是数据页的物理变化，显然undo log不是redo log的逆过程。

大 鱼, [23.01.21 19:23]
redo & undo总结
下面是redo log + undo log的简化过程，便于理解两种日志的过程：

假设有A、B两个数据，值分别为1,2.
1. 事务开始
2. 记录A=1到undo log
3. 修改A=3
4. 记录A=3到 redo log
5. 记录B=2到 undo log
6. 修改B=4
7. 记录B=4到redo log
8. 将redo log写入磁盘
9. 事务提交
实际上，在insert/update/delete操作中，redo和undo分别记录的内容都不一样，量也不一样。在InnoDB内存中，一般的顺序如下：

写undo的redo
写undo
修改数据页
写Redo
小结

大 鱼, [23.01.21 19:26]
生成时机：
事务开始之后就产生redo log，redo log的落盘并不是随着事务的提交才写入的，而是在事务的执行过程中，便开始写入redo log文件中。
释放时机：
当对应事务的脏页写入到磁盘之后，redo log的使命也就完成了，重做日志占用的空间就可以重用（被覆盖）

作者：habit_learning
链接：https://www.jianshu.com/p/59c20fdd58ba
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

大 鱼, [23.01.21 19:27]
生成时机：
事务开始之前，将当前事务版本生成 undo log，undo 也会产生 redo 来保证 undo log 的可靠性。每一次写操作都会生成 undo log，比如 update 操作，会生成一条更新前的记录信息，比如主键ID，需要更新的字段以及字段对应的旧值。对于 DELETE 操作，在 delete mark 操作时，会获取该条记录最近一次的 undo log 记录，生成的新的 undo log 记录了旧记录的 trx_id（事务编号） 和 old roll_pointer（上一个 undo log 的位置） ，这样回滚时，就可以直接找到删除之前的 undo log 进行回滚操作。
释放时机：
当事务提交之后，undo log并不能立马被删除，而是放入待清理的链表，由 purge 线程判断是否有其他事务在使用 undo 段中表的上一个事务之前的版本信息，决定是否可以清理 undo log 的日志空间。

作者：habit_learning
链接：https://www.jianshu.com/p/59c20fdd58ba
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

大 鱼, [23.01.21 19:34]
Undo Log实现
Undo Log格式
InnoDB中，undo log分为：

Insert Undo Log
Update Undo Log
Insert Undo Log
Insert Undo Log是INSERT操作产生的undo log。

INSERT操作的记录由于是该数据的第一个记录，对其他事务不可见，该Undo Log可以在事务提交后直接删除。

image

type_cmpl：undo的类型
undo_no：事务的ID
table_id：undo log对应的表对象 接着的部分记录了所有主键的列和值。

大 鱼, [23.01.21 19:34]
Update Undo Log
Update Undo Log记录对DELETE和UPDATE操作产生的Undo Log。

Update Undo Log会提供MVCC机制，因此不能在事务提交时就删除，而是放入undo log链表，等待purge线程进行最后的删除。

image

update_vector表示update操作导致发生改变的列，每个修改的列信息都要记录。对于不同的undo log类型，可能还需要记录对索引列所做的修改。

Undo Log存储管理
InnoDB基于Rollback Segment管理Undo Log，每个Rollback Segment记录1024个Undo Segment，Rollback Segment默认存储在共享表空间中。

Rollback Segment管理参数：
- innod\_undo\_directory：设置Rollback Segment文件所在的路径，默认在共享表空间内。
- innodb\_undo\_logs：设置Rollback Segment的个数，默认为128，即innoDB默认支持同事在线的事务限制为128 * 1024。
- innodb\_undo\_tablespaces：构成Rollback Segment的文件数量。
当事务没有提交时，InnoDB必须保留该事务对应的Undo Log。但是当事务提交时，依然不能删除Undo Log，因为要支持MVCC，可能有其他处于Repeatable Read隔离级别下的事务，正在读取对应版本的数据。

事务提交时，虽然不会立即删除Undo Log，但是会将对应的Undo Log放入一个删除列表中，未来通过purge线程来进行判断并删除。

本文地址：https://cheng-dp.githu

大 鱼, [24.01.21 04:11]
哈哈.机器卡曼的问题搞定了，是于360有点关系。查杀木马病毒清理机器，速度快多了，使用完毕后立即码放南山，删除360😂。这样就最大限度的降低了360引起的问题

大 鱼, [24.01.21 04:16]
360定时清理有问题可能会引起卡顿，我杀除木马病毒清理机器然后立马删除360，就不卡顿了

atiCn, [25.01.21 17:00]
方法

十十tom dom atlx akbar al rapanui十, [25.01.21 20:53]
然支付宝在国内移动支付市场是一家独大的态势，但移动支付的战争还没有结束。国内现在还有微信支付、云闪付以及京东支付等玩家在该领域发力，对于我们用户而言，这些打

大 鱼, [29.01.21 20:28]
数字转换为数字，，字符串转移单引号和反斜杠就可以了。。

大 鱼, [30.01.21 13:11]
that Metro Manila and nine other areas in the country will remain under general community quarantine (GCQ) status until January 31, 2021.

大 鱼, [01.02.21 13:47]
资金明细查询

大 鱼, [01.02.21 13:47]
Request URL: http://cadmin.88.nf/user/ajaxHuiyuanzijinmingxi.json

大 鱼, [01.02.21 13:50]
代理商模式查询

大 鱼, [01.02.21 13:50]
pageSize: 25
pageIndex: 1
sortOrder: asc
startTime: 2021-01-01 00:00:00
endTime: 2021-02-02 00:00:00
type: 
searchCondition: 2
searchValue: 1689403

大 鱼, [01.02.21 18:36]
下面是一些工作流引擎产品列表：

轻量级工作流引擎，如：Camunda，Activiti，JBoss jBPM。
BPM套件遵循“零代码”方法，如：IBM，Pega，Software AG。
带DSL的纯状态机，如：Amazon Simple Workflow，Netflix conductor。
简单的“事件反应机器”，如：IFTTT，Zapier，Microsoft Flow。
大数据或ETL的数据流框架，如：Spring Cloud数据流，Apache Airflow。
  在BPM领域有一个标准的图形化符号语言BPMN，遵循零代码或少写代码的宗旨，BPMN 2.0以后融入了BPEL，从而实现人工流和服务流程的综合调度编排

大 鱼, [07.02.21 07:15]
// 设置父类加载器 URLClassLoader classLoader = new URLClassLoader(urls, ClassGenerator.class.getClassLoader()); return Class.forName(classFullName, true, classLoader); }


作者：废物点心
链接：https://juejin.cn/post/6844903748389584909
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

大 鱼, [07.02.21 20:13]
SHOW  STATUS  LIKE  'table%';
show status like 'InnoDB_row_lock%';

大 鱼, [07.02.21 20:14]
行锁表锁情况分析

十十tom dom atlx akbar al rapanui十, [13.02.21 10:31]
Atub   202012 pay  v2  0117
#cyar  #atcyar
1130   bls 4500  pls  shuk
1202  58k  plus salary
1204  65k  to alp
350 fehar  150un
1207 bls2k pls  shk bob
1212  pt  1000  rhlg19cc
un  2k
1215  plus 3k，， plus 20k，gei klrs 17k。。
1216  bls 12k
12-1+3-12
1221  8k to krl...
1231  bls  0

十十tom dom atlx akbar al rapanui十, [13.02.21 10:31]
atv1 cashflow  202101

115  plus  40k？
117--129  5k krlv asawa
1k  jm
125  7500  19Swi cc
14k  un？117--130
130  bls  3k  pls  bob 10k

十十tom dom atlx akbar al rapanui十, [13.02.21 10:32]
atv1 cashflow  202101

115  plus  40k？
117--129  5k krlv asawa
1k  jm
125  7500  19Swi cc
14k  un？117--130
130  bls  3k  pls  bob 10k

十十tom dom atlx akbar al rapanui十, [13.02.21 13:03]
atv2  cashflow  202102
130  bls  3k  pls  bob 10k
130 should  18k

22  2k  jm rh，22  700  feolin  htl
28  bls  15k
28hlri chua rh  7500
29  bls  7k

大 鱼, [15.02.21 19:32]
[ 文件 : sms-20210215191514.xml ]

大 鱼, [15.02.21 19:33]
英语

十十tom dom atlx akbar al rapanui十, [28.02.21 10:30]
[ 文件 : sms-20210228101900.xml ]

十十tom dom atlx akbar al rapanui十, [28.02.21 17:55]
[ 文件 : sms-20210228175330.xml ]

十十tom dom atlx akbar al rapanui十, [01.03.21 14:52]
[ 文件 : 00003.vcf ]

十十tom dom atlx akbar al rapanui十, [02.03.21 11:45]
cash flow  v2
Korea cc  3k

十十tom dom atlx akbar al rapanui十, [08.03.21 22:14]
@www888888888

十十tom dom atlx akbar al rapanui十, [09.03.21 22:01]
[ 图片 ]

十十tom dom atlx akbar al rapanui十, [25.03.21 01:28]
[]
[ 相册 ]
8号技师
姓名:阿雅
年龄:19岁
身高:158
体重:45
简章:从业正规按摩2年，力度适中，性格外向，按摩认真，年龄偏小，按摩技术一般，可做额外服务，一次4000P两次6000P3次8小时8000P如做特殊服务，当次按摩免费，可按摩再做，性格乖巧听话，可要求口活，感谢喜欢她

大 鱼, [26.03.21 12:50]
[ 文件 : QiHooLoan-offical-release.apk ]

十十tom dom atlx akbar al rapanui十, [03.04.21 08:02]
[ 文件 : 00004.vcf ]

十十tom dom atlx akbar al rapanui十, [11.04.21 19:10]
@grpshwa

十十tom dom atlx akbar al rapanui十, [17.04.21 20:34]
https://t.me/familyinphp

十十tom dom atlx akbar al rapanui十, [29.04.21 09:02]
寻找食物
安东尼奥要想生存下来，第一件事就是要找到能吃的东西，当地的野生动植物中成了他的食物来源。

他说，雨林中有他一生中从未见过的野果。他看见猴子吃这些果子之后就想，如果猴子能吃，自己也应该能吃。

但是，光靠水果还是不行。他还找到了一种叫Nandu鸟的鸟蛋。安东尼奥说，这是雨林中一种很常见的鸟。它们是像鸸鹋（emu）一样不会飞的鸟，但鸟蛋很大，青绿色。

安东尼奥偶尔找到鸟蛋，生吃。他说，这是蛋白质，身体需要。

十十tom dom atlx akbar al rapanui十, [29.04.21 09:03]
避开猛兽
尽管他能找到足够的食物勉强生存，但他还需要躲避致命的毒蛇猛兽，以免成为它们的午餐。

所以，每当他停下来休息时，都把“临时住所”搭建在山顶上。

An anaconda snake wrapped round a branch in Brazil
图像来源,GETTY IMAGES
图像加注文字,
巨蟒是亚马逊的巨型食肉动物之一。

他解释说，因为美洲豹、鳄鱼和巨蟒这些动物都喜欢水，所以自己从不在水边安营。

同时，安东尼奥白天在雨林中行走时总是尽量制造很多噪音，因为他知道，白天最有可能攻击他的是受惊的动物，而不是那些早就听见他动静的动物。

十十tom dom atlx akbar al rapanui十, [29.04.21 09:31]
最初数月

你的主要担心将集中在如何保证安全饮用水的补给，避免水传疾病的感染，因为这是千百年以来人类灾祸的根源。将水烧开能有力地杀死病原体（pathogens），但该方法将消耗不少燃料。你也可以去户外野营用品店寻找净化片剂，但是，你迟早需要用点基础化学知识，来确保送进嘴里的水不会要了自己的命。

厨房用清洁漂白剂可以用来进行化学消毒，甚至游泳池内用的氯（次氯酸钠和次氯酸钙，sodium hypochlorite and calcium hypochlorite）也可以杀死细菌，起到消毒效果，但你需要将其稀释到不会毒死自己的程度。

在你学会如何制作氯之前，你也可以使用一种低科技含量方法来做水消毒：日光消毒法（solar disinfection）。这是WHO（世界卫生组织）向世界上的各个发展中国家普遍传授的方法，只需将待消毒的水装入塑料瓶，将它放置于强烈的阳光下暴晒一两天。太阳发出的紫外线会直接穿过瓶子，将瓶中的病原体杀死

十十tom dom atlx akbar al rapanui十, [29.04.21 09:42]
同寻常
最令人难以置信的是，在27年的隐居生活中奈特除了一次偶遇一名登山者，打了一声招呼外（简短的一个字Hi），没有与任何人说过一句话。

要知道，缅因州的冬天气温可以降至零下20度，但奈特说他从未生过火取暖，因为那样会很容易引起别人的注意。这简直不可思议。

芬克尔表示，别说27年，如果谁能在缅因州的冬天不点火，在薄薄的尼龙帐篷中过一个星期或一个月就足以让人肃然起敬了。

但奈特是如何做到的呢？据他本人讲，他大约在晚上7点钟就睡觉，然后定个闹表在凌晨3点钟起床，因为凌晨3点左右是夜间温度最低的时间。

所以，他通常在这时候醒来，在林中行走以保持温暖。

十十tom dom atlx akbar al rapanui十, [29.04.21 10:31]
（图片来源：Scott Stohler）

虽然客户可以通过交易指定他们在Instagram上的发帖数量，但这对夫妻对他们发表的文字和照片内容拥有最终决定权。

斯托勒夫妇表示，他们的社交媒体上大约有25%的内容是软文，虽然他们现在仍会出去拉订单，但也有公司主动找到他们。

这意味着他们多数时候都要围绕客户的目的地规划行程，而不能选择自己想去的地方。柯莱特表示，当他们出发时，"多数时候都在拍照。我们出差时很少有时间'放松'，但有时候可以在结束时（自费）增加一天的行程

十十tom dom atlx akbar al rapanui十, [29.04.21 10:53]
征上常常假借了娃娃脸的神韵。

人类社会数千年来都是一个看脸的社会。古希腊人就此发展了一门科学：“观相术”。早在公元前500年，数学家毕达哥拉斯（Pythagoras）会端详青年男子的面容，并据此判断他们能否成为好学生；没过多久，亚里士多德（Aristotle）就撰文写道：肥头大耳的人极为吝啬。当时社会上普遍认为，一个人长得像什么动物，他就是什么样的人，这种理论被视为一种上佳的识人之术。

十十tom dom atlx akbar al rapanui十, [29.04.21 10:56]
问题在于，长得像一个婴儿可能会阻碍政治家的仕途之道，使他从一开始就没法当选。人们认为娃娃脸的人较为顺从、懦弱、缺乏竞争力——而在我们的观念中，这些压根儿就不是一名领导者应有的性格特征

十十tom dom atlx akbar al rapanui十, [29.04.21 11:00]
大多数人愿意把收入的2.3%捐给慈善机构。（图片来源：Getty Images）

十十tom dom atlx akbar al rapanui十, [29.04.21 11:01]
。

波士顿大学的研究人员考虑到这一点后把收入范围缩小到1万美元至30万美元。他们发现美国人捐款占收入比惊人的一致，大致在2.3%。但是，如果你看一下收入最高的人群，即2%收入高于30万美元的人，他们的捐款平均占工资的4.4%。所以，极端富裕人群整体上在捐款方面更为慷慨。

十十tom dom atlx akbar al rapanui十, [30.04.21 07:41]
SQL语句中的一些部分，例如order by字段、表名等，是无法使用预编译语句的。这种场景极易产生SQL注入。推荐开发在Java层面做映射，设置一个字段/表名数组，仅允许用户传入索引值。这样保证传入的字段或者表名都在白名单里面。

like参数注入。使用如下SQL语句可防止SQL注入

like concat('%',#{title}, '%')，
in之后参数的SQL注入。使用如下SQL语句可防止SQL注入

1
2
3
4
id in
<foreach collection="ids" item="item" open="("separator="," close=")">
#{item} 
</foreach>

十十tom dom atlx akbar al rapanui十, [30.04.21 07:42]
mybatis-generator是mybatis官方的一款generator。在mybatis-generator自动生成的SQL语句中，order by使用的是$，也就是简单的字符串拼接，这种情况下极易产生SQL注入。需要开发者特别注意。

十十tom dom atlx akbar al rapanui十, [30.04.21 07:42]
不过，mybatis-generator产生的like语句和in语句全部都是用的参数符号#，都是非常安全的实现。

十十tom dom atlx akbar al rapanui十, [30.04.21 07:43]
前在写安全测试报告时，对于SQL注入的修复建议或者防御措施无非是两条：一是白名单限制，二是参数化查询。对于参数化查询的原理，停留于MySQL能先将SQL语句进行词法和语法解析，再将参数绑定执行的阶段。而我们在代码中用Prepared Statement语句实现参数化查询时，很可能事实并不是如此

十十tom dom atlx akbar al rapanui十, [30.04.21 07:48]
4、$方式一般用于传入数据库对象，例如传入表名.
5、一般能用#的就别用$，若不得不使用“${xxx}”这样的参数，要手工地做好过滤工作，来防止sql注入攻击。
6、在MyBatis中，“${xxx}”这样格式的参数会直接参与SQL编译，从而不能避免注入攻击。但涉及到动态表名和列名时，只能使用“${xxx}”这样的参数格式。所以，这样的参数需要我们在代码中手工进行处理来防止注入。

十十tom dom atlx akbar al rapanui十, [30.04.21 07:49]
‘1’=’1’”这样的语句），有可能入侵参数检验不足的应用程序。所以，在我们的应用中需要做一些工作，来防备这样的攻击方式。在一些安全性要求很高的应用中（比如银行软件），经常使用将SQL语句全部替换为存储过程这样的方式，来防止SQL注入。这当然是一种很安全的方式，但我们平时开发中，可能不需要这种死板的方式。

十十tom dom atlx akbar al rapanui十, [30.04.21 07:53]
ybatis框架下易产生SQL注入漏洞的情况主要分为以下三种：

1、模糊查询
Select * from news where title like ‘%#{title}%’
在这种情况下使用#程序会报错，新手程序员就把#号改成了$,这样如果java代码层面没有对用户输入的内容做处理势必会产生SQL注入漏洞。

正确写法：

select * from news where tile like concat(‘%’,#{title}, ‘%’)
2、in 之后的多个参数
in之后多个id查询时使用# 同样会报错，

Select * from news where id in (#{ids})
正确用法为使用foreach，而不是将#替换为$

id in#{ids} 
3、order by 之后
这种场景应当在Java层面做映射，设置一个字段/表名数组，仅允许用户传入索引值。这样保证传入的字段或者表名都在白名单里面。需要注意的是在mybatis-generator自动生成的SQL语句中，order by使用的也是$，而like和in没有问题

十十tom dom atlx akbar al rapanui十, [30.04.21 08:05]
#{xxx}，使用的是PreparedStatement，会有类型转换，所以比较安全；
    ${xxx}，使用字符串拼接，可以SQL注入；
    like查询不小心会有漏动，正确写法如下：
    Mysql: select * from t_user where name like concat('%', #{name}, '%')      
    Oracle: select * from t_user where name like '%' || #{name} || '%'      
    SQLServer: select * from t_user where name like '%' + #{name} + '%'

十十tom dom atlx akbar al rapanui十, [30.04.21 20:10]
水平都高,半年左右后发现这哥们其实能不用C++就不用.

水平高的程序员通常都很聪明,掌握了很棒的学习方法,学东西贼快,而且通常能快速抓到问题的重点,通常都会很多种编程语言,理解各种语言的优缺点,会权衡取舍,会在不同的场景选择合适的语言办事,不会固执的抱着一个语言当传家宝.

十十tom dom atlx akbar al rapanui十, [30.04.21 20:51]
做创业的五个国家，英国，美国，日本，德国，瑞士。

十十tom dom atlx akbar al rapanui十, [30.04.21 20:51]
最适合创业国家

十十tom dom atlx akbar al rapanui十, [30.04.21 21:10]
算他们可以找到避难所或水源的地方，他们也会害怕遇到苏拉科塔印第安人；坐牛（Sitting Bull）就是一位带领印第安人袭击达科他州马车队的首领。

十十tom dom atlx akbar al rapanui十, [30.04.21 21:10]
疯马  传奇国王人物

十十tom dom atlx akbar al rapanui十, [06.05.21 02:42]
buy买拖鞋

十十tom dom atlx akbar al rapanui十, [07.05.21 02:00]
气球胶皮用力往下拉硬币就被套进脚皮里边，然后用手指轻轻一按即可瞬间穿越，你学会了吗？没硬币在杯子外边用手指轻轻一按，瞬间穿越杯子开始教学，把硬币放在油笔上，准备一张气球胶皮用力往下拉。硬币就会套进脚皮里边，然后用手指轻轻一按即可瞬间穿越，你学会了吗？没硬币在杯子外边。

十十tom dom atlx akbar al rapanui十, [07.05.21 02:07]
这房子放在左手用食指敲打的同时扔到右手，抓住熟练以后可以拿任何物体表演，天下万物皆可消失，你学会了吗？教你在动物园给猴哥变魔术。首先准备一个猴哥喜欢吃的桃子，放在左手用食指敲打的同时扔到右手，抓住熟练以后可以拿任何物体表演，天下万物皆可消失，你学会了吗？教你在动物园给猴哥变么？

十十tom dom atlx akbar al rapanui十, [07.05.21 02:40]
就空间十年前的qq空间非主流神曲。再不要再迷恋哥。i miss  u。。。罗百即使知道要见面Sara泰国。玫瑰花办葬礼。

十十tom dom atlx akbar al rapanui十, [07.05.21 22:35]
进度推进近三年后，唐纳德·J·特朗普(Donald J. Trump)总统表示，尽管他的第一反应是撤出所有军队，但他还是会继续推进这场战争。他强调，任何撤军行动都将基于作战情况，而不是预先确定的时间表

十十tom dom atlx akbar al rapanui十, [08.05.21 09:22]
rcvtest1  she  sinbai  leicyo

十十tom dom atlx akbar al rapanui十, [08.05.21 09:22]
@rcvtest1

十十tom dom atlx akbar al rapanui十, [08.05.21 09:38]
进度  会努力不保证

十十tom dom atlx akbar al rapanui十, [08.05.21 09:39]
保安制止侵害，警察事后处理，相反

十十tom dom atlx akbar al rapanui十, [09.05.21 10:55]
rcvtest

十十tom dom atlx akbar al rapanui十, [09.05.21 10:55]
你的舍友tg发我一下。我有事问
