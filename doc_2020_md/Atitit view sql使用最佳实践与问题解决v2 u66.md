Atitit view sql使用最佳实践与问题解决


子查询返回对象问题
使用join连接  注意过滤空值

 select m.*,sc.team_id zhudui_teamid,sc_kd.team_id kedui_teamid from football_match_t m
 left join football_score_t  sc on m.id=sc.match_id and sc.team_type=1
 left join football_score_t  sc_kd on m.id=sc.match_id and sc_kd.team_type=2
where m.id=3380166 and sc.team_id>0 and sc_kd.team_id>0

，因为有单数据和条件查询问题，不能预先按照某个条件过滤连接表

Join连接一对多问题，使用过滤以及distinct解决


使用函数一个个字段链接

使用json链接
select *, json_extract(scoreObj_byTeamMatch(10000,3380166,1),'$.red_card') as scobj from football_match_t where id=3380166

DELIMITER $$

DROP FUNCTION IF EXISTS `dev_kok_sport`.`scoreObj_byTeamMatch` $$
CREATE FUNCTION `dev_kok_sport`.`scoreObj_byTeamMatch` (teamid int ,matchid int ,teamtype int) RETURNS json
BEGIN

select score,red_card into @score,@red_card from football_score_t where team_id=teamid and match_id=matchid and team_type=teamtype limit 1;
return json_object('score',@score,'red_card',@red_card);
END $$

DELIMITER ;

Othre
Fkd过滤子对象导致没有了主数据问题，，使用udf解决，或者框架子查询解决吧
View编辑自动扩展了字段怎么办，使用edit 保存下来
修改的时候加载从sql
 不好 ，，，Select × 扩展问题  可以使用自建sys views解决
Fld字段注释，使用’’ as 解决
字段结构化，使用’----------xxxx obj------------’ as  objspltor  解决
最佳实践

一个ui view 对应一个 db view

复杂条件可以使用sp
这样条件查询，只需要最简单的参数传递，但不灵活了。。

层级view exview  +ui view模式
Ex view 可以改善name以及强关联的数据。。。

Ui view对应于ui
增强 sys view 记录内外子查询

视图提供了一个用户访问的接口
，当底层表改变后，改变视图的语句来进行适应，使已经建立在这个视图上客户端程序不受影响

将安全性修改为invoker
1）在navicat上进行修改

2）通过sql语句进行修改
1 ALTER PROCEDURE proc_name SQL SECURITY INVOKER 2 ALTER PROCEDURE proc_name SQL SECURITY DEFINE
 ALTER PROCEDURE 刷新赛果 SQL SECURITY INVOKE
But refresh view fail
ALTER view foot_match_v_jinxinzhong SQL SECURITY INVOKER
补充：对于Linux，mysql等工具，操作都需要用户权限，之所以在大多数操作时，没有出现问题是因为默认是root用户，root用户具有最高权限可以操作。
但当操作某些专有的东西功能时，需要登录对应的用户信息才可以操作。
 

