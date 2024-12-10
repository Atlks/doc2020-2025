atitt多语言跨进程参数传值


    $param_rf_addr = setVal(msg);
    execSyncx($phpexe + " " + $tlghr_msg_hdl + " " + $param_rf_addr);




function setVal(val) {
    $fname = Math.random();
    writeFileSyncx("./tmp/" + $fname + ".json", JSON.stringify(msg));
    return $fname;

}




$msgg = file_get_contents(__DIR__."/tmp/". $_SERVER['argv'][1].".json");

