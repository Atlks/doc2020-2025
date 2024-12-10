Atitit 获取一列拼接为字符串 逗号分隔

 
Sql Group_contackt，但是排序只能拍一个的。。如果多个列对应排序则不行。。。


Js 使用map函数

let titFldVals = rows.map(function (e) {
    return e.dt
})

valFldVal = rows.map(function (e) {
    return e.cnt
})



Php  array_column or map或者
推荐echo json_encode( array_column($rows,'dt'));
 更加简单
Php map

$dts=array_map(
    function($item){

          return $item['dt'];
        },    $rows);

//echo $dts;
//echo json_encode($rows);
//echo json_encode($dts);

