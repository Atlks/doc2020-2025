Atitit 接口详细设计文档


设计文档
接口数据交换概述
使用通用的rest api+ json模式
数据查询使用mybatis作为数据库中间件
数据查询返回格式，使用mybatis的翻页返回的pageinfo数据或json列表

复杂查询带翻页使用的pageinfo返回。。简单查询直接返回json列表即可

{"endRow":3,"firstPage":1,"hasNextPage":true,"hasPreviousPage":false,"isFirstPage":true,"isLastPage":false,"lastPage":2,"list":[
],"navigatePages":8,"navigatepageNums":[1,2],"nextPage":2,"pageNum":1,"pageSize":3,"pages":2,"prePage":0,"size":3,"startRow":1,"total":4}

常见参数使用的含义：：
 List：：指的返回的列表数据，为 json 列表格式 

错误异常的返回会返回错误码以及错误的具体信息
异常返回也是作为json序列化返回的
错误堆栈信息stackTrace可以配置不显示在正式环境中。前端可以将此异常转化为js异常进一步处理
异常字段均来源于标准java异常格式

{
"errcode":500,
	"e":{
		"@type":"java.lang.RuntimeException",
		"localizedMessage":"参数错误",
		"message":"参数错误",
		"stackTrace":[{
			 "className":"org.chwin.firefighting.apiserver.util.ExceptionUtil",
			"fileName":"ExceptionUtil.java",
			"lineNumber":11,
			"methodName":"main",
			"nativeMethod":false
		}]
	}
	}

附：：PageInfo的方法


翻页数据与非翻页数据的区别
翻页数据有pagenum，pagesize等参数。否则为普通列表查询。。


