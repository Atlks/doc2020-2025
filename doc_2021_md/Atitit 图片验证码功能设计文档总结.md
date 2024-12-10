Atitit 图片验证码功能设计文档总结


使用图片验证码img src标签设置图片。。验证码图片有png，jpg，svg等格式。。
Svg的head是这样header('Content-Type:image/svg+xml');



大概流程是生成字串放入session。。提交的时候校验session字串即可。。。


Php png图像
<?php
//   /sdk/catchImg.php
require __DIR__ . '/../vendor/autoload.php';
use Minho\Captcha\CaptchaBuilder;

session_start();
$captch = new CaptchaBuilder();

$captch->initialize([
    'width' => 120,     // 宽度
    'height' => 40,     // 高度
    'line' => false,    // 直线
    'curve' => false,    // 曲线
    'noise' => 0,       // 噪点背景
    'fonts' => []       // 字体
]);
//  C:\wamp\bin\php\php5.6.31\php.exe composer.phar install
//C:\wamp\bin\php\php5.6.31\php.exe composer.phar update
$captch->create();
$captch->save('778.png',1);
$_SESSION['captch77'] = $captch->getText();

error_log('$_SESSION[captch77] from ctimg.php '.$_SESSION['captch77']);

$captch->output(1);
//echo $captch->getText();

Php的svg图片生成
Pnp的png图像生成测试环境遇到点问题，需要集成gd库，也依赖于os的图像库。。
所以可以使用svg格式。。可惜php没有好的svg库，，只要使用nodejs的svg库
svg-captcha
通过cli模式调用。。。

Cde
<?php
 
header('Content-Type:image/svg+xml');
session_start();

//  C:\wamp\bin\php\php5.6.31\php.exe composer.phar install
//C:\wamp\bin\php\php5.6.31\php.exe composer.phar update
$jscmd = "node cpt2.js ";    // . base64_encode(json_encode($post));
error_log( $jscmd . PHP_EOL,3,'error_log.log');
$returnContent = exec($jscmd);
error_log( '$returnContent:'.$returnContent.PHP_EOL,3,'error_log.log');

$jsonObj=json_decode($returnContent,true);
$_SESSION['captch77'] = strtolower( $jsonObj['text']);

error_log('$_SESSION[captch77] from ctimg.php is:: '.$_SESSION['captch77'].PHP_EOL,3,'error_log.log');
echo $jsonObj['data'];






const code = require("svg-captcha");
 var ret=code.create({
    size: 4,
    ignoreChars: "0o1iIl",
    noise: 0,
    color: true,
    background: "#fff",
    fontSize: 60
});
console.log(JSON.stringify(ret) )

