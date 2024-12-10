Atitit  data query lan exprs数据查询语言 查询表达式
Sql
Url str ql方便解析
   xx?from=user&name=222&age=>55
&age_op=>&age=55   这样钢筋安全
From user where name=222 and age>55

去和区分实际参数和固定参数，实用伪类法：或者关键词法
&age:op=>&age=55
From:tb=user
Css selector...    
Id ,class,tag,attr sleector..

Xml  xpath  XQuery（XML查询语言）

Url结构 ？Querystring

Qrystr=#999.userTable    or   qerstr=user#999
From user where id=999


qerstr=user[name=aaa][age=12]

From user where name=aaa and age =22


多条件复合选择
选择一个 img 标签，它含有 title 属性，并且包含类名为 logo 的元素。
img[title][class~=logo]{
...
}



