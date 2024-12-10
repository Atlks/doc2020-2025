Tp use in cmd

<?php


//   config/console.p
hp



class imptTp1129 extends think\console\Command {
    protected function configure() {
        $this->setName('calltp2')->setDescription('Here is the remark ');
    }

    protected function execute(think\console\Input $input, think\console\Output $output) {
        //$output->writeln("TestCommand:");
        var_dump(111);
    }
}


// +----------------------------------------------------------------------
// | 控制台配置
// +----------------------------------------------------------------------
return [
    // 指令定义
    'commands' => [


        'keywdReqHdlr' => 'app\common\keywdReqHdlr',
      'msgHdlrLhc' => 'app\common\msgHdlrLhc',




        'imptTp'=> '\imptTp1129',

        
    ],
];





<?php

// tpuse.php

require_once __DIR__ . "/../lib/ex.php";
loadErrHdr();
require __DIR__ . '/../vendor/autoload.php';
// 应用初始化导入tp类库
$console = (new \think\App())->console;
// $console->$catchExceptions=false;  dflt jst fas..
$console->call("imptTp");

// composer update topthink/framework
var_dump(9999);
$rows_dxds = \think\facade\Db::query("select * from db1.t1  ");
var_dump($rows_dxds);

