Atitit sparql查询问题步骤

确定from主体，，sql需要，rdf不需要wiki不需要。。
Rdf往往一个图集很少需要from，sql是多表格的
From通过某个cate属性确定 一般是性质=cat

确定属性条件  可以随便翻到最详细的一条记录，，，查看属性，
比如查看一个具体电视剧

超越语言 （Q22773934）
跳转到导航跳转到搜索
马来西亚电视剧
编辑
更多语言
配置


点击左侧的wiki数据项与查询工具Query Service

https://query.wikidata.org/#%23Cats%0ASELECT%20%3Fitem%20%3FitemLabel%20WHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP495%20wd%3AQ334.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D

打开exlain根据，随便一个查询
调整属性与属性值

查询所有新加坡电视剧


#Cats
SELECT ?item ?itemLabel ?出版日期  ?_______ ?_______Label WHERE {
  ?item wdt:P495 wd:Q334.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
  ?item wdt:P31 wd:Q5398426.
  OPTIONAL { ?item wdt:P577 ?出版日期. }
  OPTIONAL { ?item wdt:P407 ?_______. }
}
