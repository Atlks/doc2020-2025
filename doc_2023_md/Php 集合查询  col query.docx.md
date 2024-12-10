Php 集合查询  col query




Wehre 语句
$rows = $GLOBALS['bet_types'];
$row_slkted = array_filterx($rows, function ($row) {
  if ($row['玩法'] == "前后三玩法豹子")
    return true;
});
print_r($row_slkted[0]['Odds']);

Select col  array_column()
Groupby  
先 array_column()，然后去重，得到gropyb basi

gropubyCol() 


给个聚合函数传递进去。
聚合函数使用reduce计算即可。。常见的sum count都已经有了合适的函数





Selct  a,sum(b) from xx  wehre xx grouby  a.






