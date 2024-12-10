Atitit 字符串模板替换法 格式化的字符串


字符串模板 

$sql = "update merchan  set account_balance=account_balance+%d,available_balance=available_balance+%d where uname='%s' "; // .;
$sql = sprintf($sql, ,$add_amt,$add_amt,$_GET['uname']);


注意 %d 安全效验 

preg_replace

