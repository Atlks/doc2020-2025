Php grpby algo


  $rows=[
    ["betNoAmt"=>"大","Bet"=>1],
    ["betNoAmt"=>"大","Bet"=>5],
    ["betNoAmt"=>"小","Bet"=>1]
  ];
  //select bettype,cont()，sum(bet)  from xxx grpby bettype
  $rows = grpby($rows, "betNoAmt",
    function ($coll, $grpbyColVal) {
      return ["betNoAmt" => $grpbyColVal,
        "cnt" => count($coll),
        "sum" => array_sum_col("Bet", $coll)
      ];
    }

  );
  print_r($rows);
}



function grpby($rows,string $grpbyCol,   $fun) {
  $rets=[];
  $cols=arr_col_uniq($rows,$grpbyCol);

  foreach ($cols as $colVal)
  {
    var_dump($colVal);
    $coll_whereGrpcol=array_where($rows,$grpbyCol,$colVal);
    $rets[]= $fun($coll_whereGrpcol,$colVal);
  }
  return $rets;


}

function arr_col_uniq($rows, string $grpbyCol) {
  $colsVal_arr=  array_column($rows,$grpbyCol);
  $colsVal_arr= array_unique ($colsVal_arr);
  return $colsVal_arr;
}

function array_where($rows, $col, $val) {
  return  array_filterx($rows,function ($row) use($col,$val){
    if($row[$col]==$val)
      return true;
  });
}

