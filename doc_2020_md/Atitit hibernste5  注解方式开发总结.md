Atitit hibernste5  注解方式开发总结


映入hb5的jar 建立项目

建表tab1  ，这里使用了sqlite数据库

CREATE TABLE "tab1" ("column1" TEXT PRIMARY KEY, "column2" TEXT)

建立映射实体类tab1  ，主要是有@Entity  @id俩个注解表明实体和主键

package pkg;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity//声明当前类为hibernate映射到数据库中的实体类
 
//   pkg.tab1
public class tab1 {
	
	@Id
 
    private String column1;
 
	 private String column2;
	
	
	
	public String getColumn1() {
		return column1;
	}
	public void setColumn1(String column1) {
		this.column1 = column1;
	}
	public String getColumn2() {
		return column2;
	}
	public void setColumn2(String column2) {
		this.column2 = column2;
	}
	
}

Hb5 配置文件/ormHibernateDemo/src/hibernate.cfg.xml

<?xml version="1.0" encoding="UTF-8"?>
<!--
 ~ Hibernate Search, full-text search for your domain model
 ~
 ~ License: GNU Lesser General Public License (LGPL), version 2.1 or later
 ~ See the lgpl.txt file in the root directory or <http://www.gnu.org/licenses/lgpl-2.1.html>.
  -->
<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD//EN"
        "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
    <session-factory>
        <property name="hibernate.connection.driver_class">org.sqlite.JDBC</property>
        <property name="hibernate.connection.url">jdbc:sqlite:D:\\000000\\mydatabase.sqlite</property>
        <property name="hibernate.connection.username">sa</property>
        <property name="hibernate.connection.password"></property>
        
        <property name="hibernate.dialect">pkg.SQLiteDialect</property>
       
   <mapping class="pkg.tab1" />
       
    </session-factory>
    
  

</hibernate-configuration>


测试查询

public class hiberDemo {

	public static void main(String[] args) throws Exception {
	//	org.hibernate.dialect.Dialect.getDialect()
 	SessionFactory sessionFactory = new Configuration().configure("hibernate.cfg.xml").buildSessionFactory();
		
	//	SessionFactory sessionFactory = new AnnotationConfiguration().configure("hibernate.cfg.xml").buildSessionFactory();
		Session session1 =  sessionFactory.openSession();
		String sql = "select  * from tab1";
		org.hibernate.query.Query q = session1.createSQLQuery(sql);

		List li = q.list();
		System.out.println(JSON.toJSONString(li, true));
		System.out.println("ok");
		

测试保存

	tab1 tab1_rec = new tab1();
		tab1_rec.setColumn1("col111aa1");
		tab1_rec.setColumn2("col222");
	 
		
		Session session =  sessionFactory.openSession();
		
		//开启事务
		Transaction tx = session.beginTransaction();
		
		//执行添加操作
		session.save(tab1_rec);
		
		//提交事务
		tx.commit();
		
		//关闭资源
		session.close();

更新 使用update（）
删除delete
