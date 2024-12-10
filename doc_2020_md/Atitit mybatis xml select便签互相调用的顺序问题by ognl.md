Atitit mybatis xml select便签互相调用的顺序问题by ognl

package attilax.mybatis;

import lombok.SneakyThrows;
import ognl.OgnlException;
import org.chwin.firefighting.apiserver.data.MybatisUtil4game;

import java.io.IOException;

public class mybatisT {
   // @SneakyThrows
    public static void main(String[] args) throws IOException, OgnlException {


        System.out.println( MybatisUtil4game.selectList("第一个流程",null));
    }
}



<select id="第一个流程"   resultType="map"  parameterType="map">

    select "第一个流程结果";

    <bind name="name" value="@attilax.mybatis.MybatisUtil@setNextProcess('nextProcess')"/>



</select>




package attilax.mybatis;


import lombok.SneakyThrows;
import ognl.OgnlException;
import org.chwin.firefighting.apiserver.data.MybatisUtil4game;

import java.io.IOException;

//  attilax.mybatis.MybatisUtil
public class MybatisUtil {

    public static void main(String[] args) throws Exception {
        System.out.println(setNextProcess("aa"));
    }
//@SneakyThrows
    private static Object setNextProcess(String selectid_processName) throws  Exception {
        System.out.println( MybatisUtil4game.selectList(selectid_processName,null));
        return true;
    }
}





<select id="nextProcess"   resultType="map"  parameterType="map">

select "nextval";

</select>




Loading class `com.mysql.jdbc.Driver'. This is deprecated. The new driver class is `com.mysql.cj.jdbc.Driver'. The driver is automatically registered via the SPI and manual loading of the driver class is generally unnecessary.
Created connection 1267655902.
==>  Preparing: select "nextval"; 
==> Parameters: 
<==    Columns: nextval
<==        Row: nextval
<==      Total: 1
[{nextval=nextval}]
Opening JDBC Connection
Created connection 1987375157.
==>  Preparing: select "第一个流程结果"; 
==> Parameters: 
<==    Columns: 第一个流程结果
<==        Row: 第一个流程结果
<==      Total: 1
[{第一个流程结果=第一个流程结果}]

Process finished with exit code 0

问题
Bingd总是第一个执行，其他的后面执行


<select id="总流程"   resultType="map"  parameterType="map">



    <bind name="name" value="@attilax.mybatis.MybatisUtil@setNextProcess('第一个流程')"/>

    <bind name="name" value="@attilax.mybatis.MybatisUtil@setNextProcess('nextProcess')"/>

    select "最后流程";

</select>

