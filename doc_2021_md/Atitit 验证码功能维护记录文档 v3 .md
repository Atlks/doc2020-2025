Atitit 验证码功能修复总结文档


原有的tp5里面的验证码不知怎么有问题了，试图在tp5框架内修复无果。。



使用了新的验证码组件  "lifei6671/php-captcha": "0.1.*"


//C:\wamp\bin\php\php5.6.31\php.exe composer.phar update
更新下载类库

注意事项
Session获取不到需要sesion start（）开启session
Ui界面验证码获取不到，需要看下是否type为text如果为num，会忽略。。取到空。。

开启errorlog日之后，在C:\wamp\logs\php_error.log  读取日志。。对比。。

主体code

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
    'curve' => true,    // 曲线
    'noise' => 1,       // 噪点背景
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

Svg格式图片
因为png格式再测试环境依赖os的库，默认php也没有集成gd库，所以使用svg格式

Atitit 图片验证码功能设计文档总结

目录
1.1. 使用图片验证码img src标签设置图片。。验证码图片有png，jpg，svg等格式。。	1
1.2. Php png图像	1
1.3. Php的svg图片生成	2
2. Cde	3


转会png格式
测试环境已经支持，图像组件库齐全了。。
