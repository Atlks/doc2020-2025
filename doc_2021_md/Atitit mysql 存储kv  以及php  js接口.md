Atitit mysql 存储kv  以及php  js接口



CREATE TABLE `cfg`  (
  `k` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
  `typ` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
  `v` varchar(4000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
  PRIMARY KEY (`k`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;

kv_mysql.js
function  set(k,e)
{
    $.get(  "/hot_tag/get.php?k="+k, function( data ) {

        var index_data_start=data.indexOf('-----attilax---');
    
        var dataStr=data.substr(index_data_start+15);
         e   (dataStr)
    });
}


function  set(k,v,e)
{
    $.get(  "/hot_tag/set.php?k=hottag&v="+ $("#v_txtbox").val(), function( data ) {

        var index_data_start=data.indexOf('-----attilax---');

        var dataStr=data.substr(index_data_start+15);
        console.log("exe rzt:"+dataStr)
        e(dataStr)
    });
}



Set.php

<?php

header('Access-Control-Allow-Origin:*');

require "../conn.php";
$v=addslashes($_GET['v']);$k=addslashes($_GET['k']);
$sql = "REPLACE INTO    cfg set v='$v' , k='$k'";

echo $sql."\n<p>";
//$rows = queryPdo($sql, $pdo);

echo PHP_EOL . '-----------------attilax---' . PHP_EOL;
echo pdo_exec($sql);


Get.php

<?php


header('Access-Control-Allow-Origin:*');

require "../conn.php";
$k=addslashes($_GET['k']);
$sql = "select v from cfg where k='$k'";

echo $sql."\n<p>";
//$rows = queryPdo($sql, $pdo);

echo PHP_EOL . '-----------------attilax---' . PHP_EOL;
echo fetchColumnVal($sql);

