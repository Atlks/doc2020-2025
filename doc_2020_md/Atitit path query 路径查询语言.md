Atitit path query 路径查询语言  数据检索语言


List map >> spel
Html数据 》》Css选择符


Json 》map》   spel
D:\prj\sport-service\kok-sport-service\src\main\java\com\kok\sport\utils\QlSpelUtil.java


package com.kok.sport.utils;

import java.util.Map;

import org.springframework.expression.ExpressionParser;
import org.springframework.expression.spel.standard.SpelExpressionParser;
import org.springframework.expression.spel.support.StandardEvaluationContext;

public class QlSpelUtil {

	public static Object query(Map m, String expressionString) {
		ExpressionParser parser = new SpelExpressionParser();  	//1.访问root对象属性  
		 
//	  m=Maps.newConcurrentMap();
//	m.put("ret",220);


		StandardEvaluationContext context = new StandardEvaluationContext(m);  
//	context.setRootObject(null); 
		System.out.println( parser.parseExpression("#root['ret']").getValue(context));
		Object result1 = parser.parseExpression(expressionString).getValue(context);
		return result1;
	}

}


SPARQL 是RDF (the Resource Description Framework) 的查询语言
，支持长度可变的属性路径。通过允许将SPARQL 查询应用于实体，版本12 提供了强大的实体 .

Other

Ognl  xpath

