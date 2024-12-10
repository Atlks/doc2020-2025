Atitit 事务与redo 机制



Redo的整体流程
Add undolog,,,modf data,, add redo log....del undo..

重启恢复过程，
If noUndo,,alredy ok
if has undo+redo,,then its alrady ok,,del undo...
If undo+ noredo,,比较undo和当前数据，如果不同,回滚,del undo。。如果相同，没有变化，不变。。Del undo


多条事务对恢复过程。。。
If noUndo,,alredy ok



下面以一个更新事务为例，宏观上把握redo log 流转过程，如下图所示：

第一步：先将原始数据从磁盘中读入内存中来，修改数据的内存拷贝
第二步：生成一条重做日志并写入redo log buffer，记录的是数据被修改后的值
第三步：当事务commit时，将redo log buffer中的内容刷新到 redo log file，对 redo log file采用追加写的方式
第四步：定期将内存中修改的数据刷新到磁盘中
redo如何保证 事务的持久性？
InnoDB是事务的存储引擎，其通过Force Log at Commit 机制实现事务的持久性，即当事务提交时，先将 redo log buffer 写入到 redo log file 进行持久化，待事务的commit操作完成时才算完成。这种做法也被称为 Write-Ahead Log(预先日志持久化)，在持久化一个数据页之前，先将内存中相应的日志页持久化。
为了保证每次日志都写入redo log file，在每次将redo buffer写入redo log file之后，默认情况下，InnoDB存储引擎都需要调用一次 fsync操作,因为重做日志打开并没有 O_DIRECT选项，所以重做日志先写入到文件系统缓存。为了确保重做日志写入到磁盘，必须进行一次 fsync操作。fsync是一种系统调用操作，其fsync的效率取决于磁盘的性能，因此磁盘的性能也影响了事务提交的性能，也就是数据库的性能。
(O_DIRECT选项是在Linux系统中的选项，使用该选项后，对文件进行直接IO操作，不经过文件系统缓存，直接写入磁盘)
