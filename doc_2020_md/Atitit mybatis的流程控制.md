Atitit mybatis的流程控制

If while标签
配合ongl  sql 语句实现流程控制
Sql 选择 循环语句，通过命名块SP执行
调用java扩展 通过ongl spel
调用下一个selecctid

<bind name="name" value="@attilax.mybatis.MybatisUtil@setNextProcess('第一个流程')"/>
问题
获取mybatis xml ast问题，使用xml解析即可
Xml的本身即是ast的模式。。
