Atitit mybatis 简化开发与提升开发效率法


使用注解模式代替xml模式

使用通用mapper代替专用mapper

@Mapper 
 

public interface MybatisMapperCls {
 
 
    
    @Select("${sql_intag}")
    public List<Map>   query(@Param("sql_intag") String sql);
    
    @Insert("${sql_intag}")
    public int   insert(@Param("sql_intag") String sql);
    
    @Update("${sql_intag}")
    public int   update(@Param("sql_intag") String sql);
    
}

使用js等脚本语言来输出sql方便无java环境测试
通过脚本引擎解析js结果，得到sql语句
使用sp存储过程，将java mybatis部分通道化
参数传递在前端进行，中间java mybatis基本不用做代码系列了，，直接通道化，直接连接后端存储过程

注意。。为了安全性，
 限制执行sql语句的种类只能是call 和select 类型（不能包括update delete类型）
或者前端只可传递sp名称和参数 ，安全性更高

