Atitit 解析url querystr到对象

Php
parse_str( $_SERVER[ 'QUERY_STRING' ],$parr);print_r($parr);

  $json_str=json_encode($parr);
file_put_contents("C:\\data\\tisyi\\".time(), $json_str);

Java
Python

