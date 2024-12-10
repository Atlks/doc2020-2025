Atitit 性能对比记录

事务还是有用 提升20%左右。。

1.2w/min  中间事务异步模式 提升一倍啊

	"main":26298,
	"updxfinish":26298,
	"tyetytefinish":26298

可以判断中间事务是否有积压，可以使用元子类随时统计完成条数。。





异步模式  主流程业余流程分离 提升更加明显啊2倍提升    1.2w/min
2w/30s    4w/3min





Mltqry合并三条语句提升 20%
线程对比   单线程更快 3倍差距。。。
流失(a)vs 客户端游标（aa 俩倍差距）

流失 单线程 6k/min    18w  3M20s
流失 单线程  6k/min


多线程     2k/min       1k/30s

Ori     11k/min   5.5k/30s







Ori   1w lmt.....    10k/min   5k/30s












最上面单线程1w客户端游标 恢复到同步模式和非multiquery模式   

非multiquery模式4k/min        2k  30s









Mltqry  mode (impt)提升一倍  7k/min    3.5k/30s




优先级排序模式 提升30%，从7k到10k

天天分钱优先级排序放后

最新只改动multisql   4k/min

























5k、min  mltqry+dbutil









Ori   split sql mode   4k/min






Mybatis+mltqry    6k/min






Mybatis update  not selectlist  mode...  6k/min






原因应该是mybatis有缓存。。或强制事务了？


开启事务后，err 只有 800/min 了。垃圾





Dbutil+ Trans ok....6k/min








Flush log time out =5  ,,no effect  6k/min




