Atitit php多语句sql执行 exec

  $pdo->setAttribute(PDO::ATTR_EMULATE_PREPARES, 0);
Not ok..maybe only use exec(),,cant query()

Mault mult query is ok...

echo pdo_exec("set @t=777")."\n";

$rows = queryPdo("select @t", $pdo);

 echo PHP_EOL.'-----------------attilax---'.PHP_EOL;
echo json_encode($rows);



function pdo_exec($sql )
{
    global $main;
    var_dump_ati( PHP_EOL . $sql . PHP_EOL );
    //  $main->info($sql);
    global $glb;
    $glb['sql'] = $sql;
    var_dump_ati($glb);
    global $pdo; //use global var
   return  $pdo->exec($sql);




    // return array($pdo, $rows);
}

