Atitit 数据库连接池druid使用

Druid 打印可执行 SQL | Mr.Kail's Blog


 /*
         * Druid 配置
         */
        Properties config = new Properties();
        // Loading class `com.mysql.jdbc.Driver'. This is deprecated.
        // The new driver class is `com.mysql.cj.jdbc.Driver'.
        // The driver is automatically registered via the SPI and manual loading of the driver class is generally unnecessary.
        // config.setProperty(DruidDataSourceFactory.PROP_DRIVERCLASSNAME, "com.mysql.jdbc.Driver");
        config.setProperty(DruidDataSourceFactory.PROP_DRIVERCLASSNAME, "com.mysql.cj.jdbc.Driver");
        config.setProperty(DruidDataSourceFactory.PROP_URL, "jdbc:mysql:///test");
        config.setProperty(DruidDataSourceFactory.PROP_USERNAME, "xxx");
        config.setProperty(DruidDataSourceFactory.PROP_PASSWORD, "xxx");

        DruidDataSource dataSource = (DruidDataSource) DruidDataSourceFactory.createDataSource(config);
        // 设置过滤器
        dataSource.setProxyFilters(Collections.singletonList(slf4jLogFilter));


        /*
         * JDBC 操作 -- 无需关注
         */
        Connection conn = dataSource.getConnection();

