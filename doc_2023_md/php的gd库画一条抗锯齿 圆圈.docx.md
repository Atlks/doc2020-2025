php的gd库画一条抗锯齿 圆圈


php中文网
发布： 2016-06-13 13:32:42
原创
1925人浏览过
如何使用php的gd库画一条抗锯齿的粗斜线?
如题，使用多边形画的填充图是有锯齿的
。imageantialias函数是无效的。


------解决方案--------------------
点阵图有锯齿是必然的
imageantialias 的抗锯齿是有作用的，你可以对比他打开和关闭时的效果
如果你对 imageantialias 的效果不满意（毕竟GD不是专业的图像处理包），那就要你自己编程解决了


在许多情况下，网站需要动态创建图像：饼图、圆角、菜单按钮等。这个列表是无穷无尽的。 PHP，或更准确地说是 GD 库，提供填充椭圆弧和椭圆，但它们没有抗锯齿。因此，我编写了一个 PHP 函数，可以轻松地使用 PHP 渲染填充抗锯齿椭圆弧或填充抗锯齿椭圆（以及圆..）。现在绘制这些填充的弧线是单线。


为了快速而肮脏的抗锯齿，请将
图像设为所需尺寸的两倍，然后将采样缩小到所需尺寸。
为了快速而肮脏的抗锯齿，请将图像设为所需尺寸的两倍，然后将采样缩小到所需尺寸。


/**
*
* //为了快速而肮脏的抗锯齿，请将图像设为所需尺寸的两倍，然后将采样缩小到所需尺寸。
* @param $imageX2
* @param int $width
* @param $color
* @return false|GdImage|resource
*/
function imagefilledellipseX($img, $center_x, $center_y, int $width,$height, $color) {


 $bg_tomin = imagecolorallocatealpha($img, 0, 0, 0, 127);

 $bigPicWd = $width * 2 + 1;//msut add 1 offset,,beir not full
 $imageX2 = imagecreatetruecolor($bigPicWd, $bigPicWd);
 imagefill($imageX2, 0, 0, $bg_tomin); //这里的 "0, 0"是指坐标, 使用体验就类似 Windows 系统"画图"软件的"颜料桶", 点一下之后, 在整个封闭区间内填充颜色

//  $bg_clr = imagecolorallocate($imageX2, 0, 0, 0);

 $colr_red = imagecolorallocate($imageX2, 204, 0, 0);


 imagefilledellipse($imageX2, $width, $width, $width * 2, $width * 2, $color);
// imagepng($imageX2, __DIR__ . "/../public/trend_resmp_bgCyk.jpg");
//-----------------
 // $imageOut = imagecreatetruecolor($width, $width);
 imagecopyresampled($img, $imageX2, $center_x-($width/2), $center_y-($width/2), 0, 0, $width, $width, $bigPicWd, $bigPicWd);

}


$circleSize=90;
$canvasSize=100;

$imageX2 = imagecreatetruecolor($canvasSize*2, $canvasSize*2);

$bg = imagecolorallocate($imageX2, 255, 255, 255);

$col_ellipse = imagecolorallocate($imageX2, 204, 0, 0);

imagefilledellipse($imageX2, $canvasSize, $canvasSize, $circleSize*2, $circleSize*2, $col_ellipse);

$imageOut = imagecreatetruecolor($canvasSize, $canvasSize);
imagecopyresampled($imageOut, $imageX2, 0, 0, 0, 0, $canvasSize, $canvasSize, $canvasSize*2, $canvasSize*2);

header("Content-type: image/png");
imagepng($imageOut);

