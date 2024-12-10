Atitit 基于内存存储对undo于事务实现引擎

业务相关

Try catch

如果add ,那么delte 根据Pk
如果updt，那么恢复原来对数据。。一般也就一俩个字段，保存在变量里面即可
如果dlt  那么 add回原来。。逻辑删除更加简单。。Updt tag即可

存储为Json对象字符串更加方便


