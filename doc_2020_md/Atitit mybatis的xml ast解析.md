Atitit mybatis的xml ast解析

使用拦截器拦截mapperStatment


  public Object intercept(Invocation invocation) throws Throwable {
        System.out.println("PageInterceptor -- intercept");


        if (invocation.getTarget() instanceof StatementHandler) {
            StatementHandler statementHandler = (StatementHandler) invocation.getTarget();
            BoundSql BoundSql1=  statementHandler.getBoundSql();
            String sql = BoundSql1.getSql();

            System.out.println(sql);


            RoutingStatementHandler rsh=(RoutingStatementHandler)statementHandler;



            MetaObject MetaObject1 = SystemMetaObject.forObject(statementHandler);
            MappedStatement mappedStatement = (MappedStatement) MetaObject1.getValue("delegate.mappedStatement");
            String selectId = mappedStatement.getId();
        DynamicSqlSource dss= (DynamicSqlSource) mappedStatement.getSqlSource();
        //dss.getRootSqlnode
        Object o=    MetaObject1.getValue("delegate.mappedStatement.sqlSource.rootSqlNode.contents");
        //    MixedSqlNode msn= (MixedSqlNode) o;

            List<SqlNode> li_sqwlnote= (List<SqlNode>) o;
                //    ifsqlno
            System.out.println(o);
//
//
//          //      metaStatementHandler.setValue("delegate.boundSql.sql", pageSql);
//
throw new RuntimeException("break");





