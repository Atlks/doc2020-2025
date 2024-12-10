Atitit spring spring mybatis 整合查询


Atitit spring spring mybatis 整合查询
import org.apache.ibatis.session.RowBounds;
import org.mybatis.spring.support.SqlSessionDaoSupport;
import org.springframework.jdbc.core.JdbcTemplate;

import com.cnhis.cloudhealth.commons.utils.BaseVO;
import com.cnhis.cloudhealth.commons.utils.Page;
import com.cnhis.cloudhealth.commons.utils.YHDCollectionUtils;

public abstract class BaseDao extends SqlSessionDaoSupport {
Atitit spring spring mybatis 整合查询
	/**
	 * 功能：向数据库中插入一条数据记录
	 * @param sqlDef	sql语句的定义名称
	 * @param vo		VO对象
	 * @return	VO对象
	 */
	public  Object  insert(String  sqlDef,Object vo)throws Exception{
		getSqlSession().insert(sqlDef,vo);
		return  vo;
	}



public abstract class SqlSessionDaoSupport extends DaoSupport {

  public final SqlSession getSqlSession() {
    return this.sqlSession;
  }
