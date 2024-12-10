Atitit 提升mybatis与sql可读性


Hadlertype太长，貌似不能指定别名，智能指定javatype解决 ？？

使用变量解决sql可读性

set @source='人工';
insert task_warning(place,Source,HiddenDescript,LivePhoto,Type,ProblemReporter ,TaskName )
VALUES(#{place},@source,#{HiddenDescript},#{LivePhoto},#{Type},#{ProblemReporter} ,#{TaskName});

