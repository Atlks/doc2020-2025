Tpx use prblm


How to use in console

Must in namespace think and ...ini     new app() just ok..

#!/usr/bin/env php
<?php
namespace think;

echo  111;
// 命令行入口文件
// 加载基础文件
require __DIR__ . '/vendor/autoload.php';

// 应用初始化
(new App())


// 命令行入口文件
// 加载基础文件
require __DIR__ . '/vendor/autoload.php';

// 应用初始化
(new App())->console->run();

