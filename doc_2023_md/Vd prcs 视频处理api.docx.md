Vd prcs 视频处理api





//截取当前视频图片

$cmd="$ffmpeg -i $iptFlv   -frames:v 1 foobar.jpeg";


视频拆分为图片

ffmpeg     -i http://h1. gvideo12_2.flv -f image2 -vf fps=9 -y  $vddir%08d.jpg




mltpic2vd

function mltpic2vd($ffmpeg, $picdr, $outf): void {
 log_enterMethV2(__METHOD__,func_get_args(),"vdcvt");

 $ffmpeg="C:\\ffmpeg-2023-12-11-git-1439784ff0-essentials_build\\bin\\ffmpeg.exe";
 $cmd = "$ffmpeg -f image2 -r 10 -i $picdr%d.jpg  $outf";
 echo $cmd . "\r\n";
// $cmd="php ".__DIR__."/../pic2vd.php";
 logV3(__METHOD__,$cmd,"vdcvt");
 exec($cmd);
}

