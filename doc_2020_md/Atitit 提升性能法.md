Atitit 提升性能法 ---物化视图


物化视图的类型：ON DEMAND、ON COMMIT

    二者的区别在于刷新方法的不同，ON DEMAND顾名思义，仅在该物化视图“需要”被刷新了，才进行刷新(REFRESH)，即更新物化视图，以保证和基表数据的一致性；而ON COMMIT是说，一旦基表有了COMMIT，即事务提交，则立刻刷新，立刻更新物化视图，使得数据和基表一致。

物化视图的刷新   刷新的方法有四种：FAST、COMPLETE、FORCE和NEVER

    刷新（Refresh）：指当基表发生了DML操作后，物化视图何时采用哪种方式和基表进行同步。刷新的模式有两种：ON DEMAND和ON COMMIT。（如上所述）
    刷新的方法有四种：FAST、COMPLETE、FORCE和NEVER。FAST刷新采用增量刷新，只刷新自上次刷新以后进行的修改。COMPLETE刷新对整个物化视图进行完全的刷新。如果选择FORCE方式，则Oracle在刷新时会去判断是否可以进行快速刷新，如果可以则采用FAST方式，否则采用COMPLETE的方式。NEVER指物化视图不进行任何刷新。
     对于已经创建好的物化视图，可以修改其刷新方式，比如把物化视图mv_name的刷新方式修改为每天晚上10点刷新一次：alter materialized view mv_name refresh force on demand start with sysdate next to_date(concat(to_char(sysdate+1,'dd-mm-yyyy'),' 22:00:00'),'dd-mm-yyyy hh24:mi:ss')
