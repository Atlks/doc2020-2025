Atitit 配置文件的双向同步功能

远程更新单个文件的功能..
使用upload.html  解决...

双向同步配置,需要知道哪些配置修改了,根据时间判断..然后下载对应的文件配置即可..
列出制定目录所有文件,以及修改时间属性..

<?php
$dir = __DIR__ . "/../application/extra";
var_dump($dir);
$dirArr = scandir($dir);
var_dump($dirArr);
foreach($dirArr as $v){
//组合文件或文件夹的路径
 

    if ($v != '.' && $v != '..'){


// web abslt path
   $dirname ='/application/extra';
    $filename = $dirname.'/'.$v;
        echo $filename."\n<p>";

        $disk_path=__DIR__ . "/../application/extra/".$v;

        $tm=filectime($disk_path);
           echo "创建时间：".date("Y-m-d H:i:s",$tm)."\n<p>";
           echo "<a href='down.php?file=$filename' >down</a><p>\n";
    }


}


