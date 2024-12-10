Simple db  PouchDB uses LevelDB 



In Node.js, PouchDB uses LevelDB under the hood, and also supports many other backends via the LevelUP ecosystem.



leveldb是一个写性能十分优秀的存储引擎，是典型的LSM树(Log Structured-Merge Tree)实现。LSM树的核心思想就是放弃部分读的性能，换取最大的写入能力。
LSM树写性能极高的原理，简单地来说就是尽量减少随机写的次数。对于每次写入操作，并不是直接将最新的数据驻留在磁盘中，而是将其拆分成（1）一次日志文件的顺序写（2）一次内存中的数据插入。leveldb正是实践


从历史上看，JavaScript不与数据库集成，尽管这种情况已经开始发生变化。
PouchDB是JavaScript数据库的一个例子。


