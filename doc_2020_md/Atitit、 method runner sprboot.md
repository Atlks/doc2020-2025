Atitit、 method runner sprboot

启动springoot，获得context，，注入县官bean，，然后使用普通的即可

package com.kok.sport.utils.ql;

import org.apache.ibatis.session.SqlSessionFactory;
import org.springframework.expression.Expression;
import org.springframework.expression.ExpressionParser;
import org.springframework.expression.spel.standard.SpelExpressionParser;

import com.kok.SportApplication;
import com.kok.sport.utils.CaptchData;
import com.kok.sport.utils.MybatisMapper;

public class MethodRunnerSpringboot {

	// T(com.kok.sport.utils.CaptchData).m1() invoke sttatic method
	// T(com.kok.sport.utils.CaptchData).Football_Basic_Update_profile()
	public static void main(String[] args) throws Throwable {
		System.out.println(args[0]);
		System.out.println("d");
		String e = args[0];

//		Interpreter i = new Interpreter(); // Construct an interpreter
//		System.out.println(i.eval(" com.kok.sport.utils.CaptchData.m1()  "));
		ExpressionParser parser = new SpelExpressionParser();

		Expression exp = parser.parseExpression(e);

		//lauch sprinboot main
		SportApplication.main(args);
		
		//inject to the class 
		MybatisMapper MybatisMapper1 = SportApplication.context.getBean(MybatisMapper.class);
		SqlSessionFactory sqlSessionFactory = SportApplication.context.getBean(SqlSessionFactory.class);
		System.out.println(MybatisMapper1.querySql("select 'frm MethodRunnerSpringboot'"));
		CaptchData.MybatisMapper1 = MybatisMapper1;
		CaptchData.sqlSessionFactory = sqlSessionFactory;
		

		System.out.println(exp.getValue());

	}

}

