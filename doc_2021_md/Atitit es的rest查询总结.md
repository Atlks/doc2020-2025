Atitit es的rest查询总结


Es的查询

任意一个查询后再加上 ?pretty 就可以生成 更加美观 的JSON反馈，以增强可读性。
请求表结构元数据GET /db/table/_source


//创建索引用put ip:9200/person


{


"settings":{


"number_of_shards":3,


"number_of_replicas":1


},


"mappings":{


"man":{


"properties":{


"name":{


"type":"text"


},


"age":{


"type":"integer"


}


}


}


}


}



查询表按照条件where


//自动id添加文档post ip:9200/person/man


{


"name":"111",


"age":11


}






//doc修改post ip:9200/person/man/1/_update


{


"doc":{


"name":"大大阿达"


}


}



//删除文档delete ip:9200/person/man/1


查询


//根据id查询文档get ip:9200/person/man/1



//根据条件查询分页 排序post ip:9200/person/man/_search


{


"query":{


"match":{


"name":"zzz"


},


"from":1,


"size":5,


"sort":[


"age":{


"order":"desc"


}


]


}


}



//查询全部 post ip:9200/person/man/_search


{


"query":{


"match_all":{}


}


}



//分组查询post ip:9200/person/man/_search


{


"aggs":{


"group_by_age":{


"terms":{


"field":"age"


}


}


}


}



//聚合 多行函数(也可单个max,min) post ip:9200/person/man/_search


{


"aggs":{


"many_function":{


"stats":{


"field":"age"


}


}


}


}



Ref
ES的RESTful API 一些常用操作_Dream的博客-CSDN博客
