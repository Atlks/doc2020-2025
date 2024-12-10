Atitit 文件上传下载 php  

<form action="upload.php" enctype="multipart/form-data" method="post">
update path: <input type="text" name="path1"></input>
<input type="file" name="file1"></input><br>
<button>sumt</button>
</form>

C:\wamp\www\nzsp1_cms\file\upload.html
C:\wamp\www\nzsp1_cms\file\upload.php
C:\wamp\www\nzsp1_cms\file\down.php

<?php

$name = $_FILES['file1']['name']; // 客户端机器文件的原名称
$tmpPath = $_FILES['file1']['tmp_name'];
echo $name;
echo "\n<br>   file name:" . $name . "\n<br>";
echo "\n<br>   tmpPath:" . $tmpPath . "\n<br>";

/**  //其实我们在上传文件时，点击上传后，数据由http协议先发送到apache服务器那边，这里apache服务器已经将上传的文件存放到了服务器下的C:\windows\Temp目录下了。这时我们只需转存到我们需要存放的目录即可。
 *
 * $tmpPath = $value['tmp_name'];
 *      $tmpType = $value['type'];
 *      $tmpSize = $value['size']
 */

//我们给每个用户动态的创建一个文件夹
$user_path = __DIR__ . "/.." . $_POST['path1'];
//判断该用户文件夹是否已经有这个文件夹
if (!file_exists($user_path)) {
    mkdir($user_path);
}
//中文路径名  文件名
$new_file = $user_path . "/" . $name;
echo "\n<br> new file name:" . $new_file . "\n<br>";
$to = iconv("utf-8", "gbk", $new_file);
//iconv not effect
var_dump(($to));
move_uploaded_file($tmpPath, $to);


Down

<?php
error_reporting(E_ALL & ~E_NOTICE & ~E_WARNING);
//接收需要下载的文件名称
if (!isset($_GET['file'])) exit('Filename is empty');
if (empty($_GET['file'])) exit('Filename not valid');
ob_clean();//清除一下缓冲区
//获得文件名称
$filename = basename(urldecode($_GET['file']));
error_log('$filename '. $filename);
//文件完整路径（这里将真实的文件存放在temp目录下）
$filePath = __DIR__ . "/../" .$_GET['file'];
error_log('$filePath '. $filePath);
//将utf8编码转换成gbk编码，否则，文件中文名称的文件无法打开
$filePath = iconv('UTF-8', 'gbk', $filePath);
//检查文件是否可读
if (!is_file($filePath) || !is_readable($filePath)) exit('Can not access file ' . $filename);
/**
 *
 * /application/extra/maccms.php
 * 这里应该加上安全验证之类的代码，例如：检测请求来源、验证UA标识等等
 */
//以只读方式打开文件，并强制使用二进制模式
$fileHandle = fopen($filePath, "rb");
if ($fileHandle === false) {
    exit("Can not open file: $filename");
}
//文件类型是二进制流。设置为utf8编码（支持中文文件名称）
header('Content-type:application/octet-stream; charset=utf-8');
header("Content-Transfer-Encoding: binary");
header("Accept-Ranges: bytes");
//文件大小
header("Content-Length: " . filesize($filePath));
//触发浏览器文件下载功能
header('Content-Disposition:attachment;filename="' . urlencode($filename) . '"');
//循环读取文件内容，并输出
while (!feof($fileHandle)) {
    //从文件指针 handle 读取最多 length 个字节（每次输出10k）
    echo fread($fileHandle, 10240);
}
//关闭文件流
fclose($fileHandle);

