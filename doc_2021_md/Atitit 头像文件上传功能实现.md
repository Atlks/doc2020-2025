Atitit 头像文件上传功能实现

‘
上传文件原理

 //其实我们在上传文件时，点击上传后，数据由http协议先发送到apache服务器那边，这里apache服务器已经将上传的文件存放到了服务器下的C:\windows\Temp目录下了。这时我们只需转存到我们需要存放的目录即可。
界面ui

    <form action="upload.php" enctype="multipart/form-data" method="post" style="max-width: 375px;width: 100%;">
  <a href="javascript:file1.click()">
          <img id="img1" src="../app_login/149071.png" style="width: 100px;border-radius: 99px;height: 100px" />
        </a>
        <input type="file" id="file1" style="display: none;" onchange="readFile()"></input>
        <script>
function readFile(){ 
   
    var reader = new FileReader(); 
  
    reader.onload = function(e){ 
      console.log(e)
      //// convert image file to base64 string
     img1.src=reader.result
      
    } 

    const file = document.querySelector('input[type=file]').files[0];
    reader.readAsDataURL(file); 
} 

        </script>
        <br>
        点击更换头像



预览实现

        <input type="file" id="file1" style="display: none;" onchange="readFile()"></input>
        <script>
function readFile(){ 
   
    var reader = new FileReader(); 
  
    reader.onload = function(e){ 
      console.log(e)
      //// convert image file to base64 string
     img1.src=reader.result
      
    } 

    const file = document.querySelector('input[type=file]').files[0];
    reader.readAsDataURL(file); 
} 


保存头像文件php


<?php

$_POST['path1']="/headpic/"
$name = $_FILES['file1']['name']; // 客户端机器文件的原名称
$tmpPath = $_FILES['file1']['tmp_name'];
echo $name;
echo "\n<br>   file name:" . $name . "\n<br>";
echo "\n<br>   tmpPath:" . $tmpPath . "\n<br>";

/**  //其实我们在上传文件时，点击上传后，数据由http协议先发送到apache服务器那边，这里apache服务器已经将上传的文件存放到了服务器下的C:\windows\Temp目录下了。这时我们只需转存到我们需要存放的目录即可。
 *
 * $tmpPath = $value['tmp_name'];
 *      $tmpType = $value['type'];
 *      $tmpSize = $value['size']
 */

//我们给每个用户动态的创建一个文件夹
$user_path = __DIR__ . "/.." . $_POST['path1'];
//判断该用户文件夹是否已经有这个文件夹
if (!file_exists($user_path)) {
    mkdir($user_path);
}
//中文路径名  文件名
$new_file = $user_path . "/" . $name;
echo "\n<br> new file name:" . $new_file . "\n<br>";
$to = iconv("utf-8", "gbk", $new_file);
//iconv not effect
var_dump(($to));
move_uploaded_file($tmpPath, $to);


保存文件nodejs  java

Atitit 上传文件（图片 视频 音乐 其他文件  流程



Ref
Atitit .h5文件上传 v3
Atitit linux ssh2 sftp  命令行上传文件
curl上传
Atitit webdav big file up solu大文件上传的解决方案
在线文件管理方案模式
