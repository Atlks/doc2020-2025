Atitit mybatis业务流程配置化管理总结

Mybatis
MyBatis 是支持定制化 SQL、存储过程以及高级映射的优秀的持久层框架
也对业务流程 配置化管理作出了很大贡献，使用的xml模式配置编写代码 极大的增强了扩展性，业务调整的灵活性。。基本上达到了较好的 新建更改业务逻辑 动态化配置
可以看作一个简化版业务逻辑流程引擎

流程模型常见的bpm模式
活动task 流程，getway流程控制(分支跳转 循环等）

建立与操作实体
Mybatis操作的实体基本是sql数据库表实现的实体，或者map，xml等实现的实体
使用sql xml来操作它们

表单绑定
通常使用ajax 模式传递数据，，使用java等语言来传递绑定数据到mybatis
表单跳转一般前端js实现了，更加灵活度	
建立业务流程
常使用《select标签，适合大多数流程

   <select id="上报隐患流程" parameterType="Map" resultType="Map">
        set @source = '人工';
        insert task_warning(place, Source, HiddenDescript, LivePhoto, Type, ProblemReporter, TaskName)
                VALUES (#{place}, @source, #{HiddenDescript}, #{LivePhoto}, #{Type}, #{ProblemReporter}, #{TaskName});
        insert workorder(TaskName,Descript,Property,warnId)values (#{TaskName},#{Descript},#{Property},LAST_INSERT_ID());
        set @loginfo = json_object('place', #{place}, 'source', @source, 'HiddenDescript', #{HiddenDescript}, 'TaskName',     #{TaskName});
        insert oplog(oper, event)  values (#{ProblemReporter}, @loginfo);

        /*
   select LAST_INSERT_ID()
SELECT ROW_COUNT() as cnt;
            //select LAST_INSERT_ID()*/
    </select>


Update insert 标签更简单，但是不能返回复杂数据，适合于简单流程使用
流程控制
顺序流程（略
选择流程 xml语言标签if choose


if
choose (when, otherwise)
循环流程foreach
也可结合sql的流程控制

函数扩展
语言扩展
1.1.默认，mybatis使用xml，sql等语言来书写业务流程

使用java扩展函数，，2.1.1.TypeHandler概念 

Mybatis默认采用ONGL解析参数，所以会自动采用对象树的形式

插件（plugins）扩展拦截
MyBatis 允许你在已映射语句执行过程中的某一点进行拦截调用。默认情况下，MyBatis 允许使用插件来拦截的方法调用包括：
Executor (update, query, flushStatements, commit, rollback, getTransaction, close, isClosed)
ParameterHandler (getParameterObject, setParameters)
ResultSetHandler (handleResultSets, handleOutputParameters)
StatementHandler (prepare, parameterize, batch, update, query)


异常处理
其他
子流程  使用sql标签标注

sql – 可被其他语句引用的可重用语句块。
事件机制 （略
Gui图形化流程设计（略


ref

初学者的BPMN教程 - BPMN for Beginners.html
Atitit mybatis的扩展使用sql udf,js java等语言

