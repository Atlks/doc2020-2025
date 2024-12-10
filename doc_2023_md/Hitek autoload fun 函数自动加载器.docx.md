Hitek autoload fun 函数自动加载器

设就远离pricpl ，扫描给定的类库名称和include目录去加载即可。。



调用指南



require ("./autoload.js")


echo(99999999999999)

console_log(444)

仿照php的fun autoload implt

C:\modyfing\bot\lib\autoloadx.php

Js fun loader can multi load...not show fun redcra....looks better than php
加载器内部实现


global['__DIR__']=__dirname;
global['$GLOBALS']=[];


require('./file.js');

function iniAutoload3($libs,$dirs307)
{
 //  ob_start();
   require ("./php.js");

   var fs=require("fs")
   $logdir = __DIR__ + "/../../runtime/";
   $GLOBALS['logdir'] = $logdir;
  // require_once __DIR__ . "/../app/common/betstr.php";
 //  $dirs307 = '/';    //   /../../lib/,/../lib/,/lib/,
   $arr_dirs = explode(",", $dirs307);

   for (const $dir of $arr_dirs) {

       $arr_libs307=$libs.split(",");
       for (const $libnm of $arr_libs307) {

           $fname =$dir+ "/"+$libnm+".js"  ;
          // console.log($fname);
           if (!file_exists($fname))
               continue;
           require_once ($fname);
       }
   }


  // ob_end_clean();
}
global['iniAutoload3']=iniAutoload3;
iniAutoload3("php,str,time,fun,var,aes,dsl,enc,file,http",".,..,../libx,../libBiz");

