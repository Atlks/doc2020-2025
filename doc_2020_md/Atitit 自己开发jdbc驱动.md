Atitit 自己开发jdbc驱动

D:\0wkspc\platform-top-run-coffey\platform-top-service\platform-top-service-finance\src\main\java\attilax\mybatis\MysqlDriver4dbg.java

package attilax.mybatis;

import attilax.sqlImpt.ConnectionImp;
import attilax.sqlImpt.PreparedStatementImp;
import attilax.sqlImpt.StatementImp;

import java.io.InputStream;
import java.io.Reader;
import java.math.BigDecimal;
import java.net.URL;
import java.sql.*;
import java.util.Calendar;
import java.util.Map;
import java.util.Properties;
import java.util.concurrent.Executor;
import java.util.logging.Logger;

//   attilax.mybatis.MysqlDriver4dbg
public class MysqlDriver4dbg  implements Driver {


    static {
        try {
            DriverManager.registerDriver(new MysqlDriver4dbg());
        } catch (SQLException var1) {
            throw new RuntimeException("Can't register driver!");
        }
    }
    @Override
    public Connection connect(String url, Properties info) throws SQLException {
        return new ConnectionImp() ;
    }

    @Override
    public boolean acceptsURL(String url) throws SQLException {
        return false;
    }

    @Override
    public DriverPropertyInfo[] getPropertyInfo(String url, Properties info) throws SQLException {
        return new DriverPropertyInfo[0];
    }

    @Override
    public int getMajorVersion() {
        return 0;
    }

    @Override
    public int getMinorVersion() {
        return 0;
    }

    @Override
    public boolean jdbcCompliant() {
        return false;
    }

    @Override
    public Logger getParentLogger() throws SQLFeatureNotSupportedException {
        return null;
    }
}




package attilax.sqlImpt;

import lombok.SneakyThrows;

import java.sql.*;

import static com.alibaba.druid.sql.parser.Token.BY;

public class mysqlJDbcT {

    public static void main(String[] args) throws Exception {
        //1.加载驱动
        Class.forName("attilax.mybatis.MysqlDriver4dbg");

        String url = "jdbc:atidb://xxx.db";

        String user = "root";

        String password = "123456";
        //2.建立连接
        Connection connections = DriverManager.getConnection(url, user, password);
        //返回连接对象
        //3.准备SQL语句
        PreparedStatement pStatement = connections.prepareStatement("select 1");
        //4.执行SQL语句
        ResultSet resultSet = pStatement.executeQuery();


        while (resultSet.next()) {
            System.out.println(resultSet.getString(0));

        }

    }
}



package attilax.sqlImpt;

import java.sql.*;
import java.util.ArrayList;
import java.util.HashMap;

public class mysqlJDbcT {

    public static void main(String[] args) throws Exception {
        //1.加载驱动
        Class.forName("attilax.mybatis.MysqlDriver4dbg");

        String url = "jdbc:atidb://xxx.db";

        String user = "root";

        String password = "123456";
        //2.建立连接
        Connection connections = DriverManager.getConnection(url, user, password);
        //返回连接对象
        //3.准备SQL语句
        Statement pStatement = connections.createStatement(  );
        if(pStatement instanceof  StatementImp)
        {
            StatementImp PreparedStatementImp1= (StatementImp) pStatement;
            PreparedStatementImp1.li_full =(new ArrayList(){{
                this.add(    new HashMap(){{
                    this.put("age",18);
                }});
                this.add(    new HashMap(){{
                    this.put("age",19);
                }});
            }});
        }
        //4.执行SQL语句
        ResultSet resultSet = pStatement.executeQuery("select 1");


        while (resultSet.next()) {

            System.out.println(resultSet.getString("age"));

        }

    }
}

