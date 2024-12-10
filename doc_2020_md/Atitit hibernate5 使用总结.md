Atitit hibernate5 使用总结


/ormHibernateDemo/src/hibernate.cfg.xml

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
       
 
       
    </session-factory>

</hibernate-configuration>





package pkg;

import java.util.List;

import org.hibernate.HibernateException;
import org.hibernate.Query;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

import com.alibaba.fastjson.JSON;

public class hiberDemo {

	public static void main(String[] args) throws Exception {
	//	org.hibernate.dialect.Dialect.getDialect()
		SessionFactory sessionFactory = new Configuration().configure("hibernate.cfg.xml").buildSessionFactory();
		Session session1 = sessionFactory.openSession();
		String sql = "select  * from tab1";
		org.hibernate.query.Query q = session1.createSQLQuery(sql);

		List li = q.list();
		System.out.println(JSON.toJSONString(li, true));
		System.out.println("ok");
	}

}

