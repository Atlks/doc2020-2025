自己实现html渲染过程bp最佳实践


HTML 代码转化成 DOM
CSS 代码转化成 CSSOM（CSS Object Model）
结合 DOM 和 CSSOM，生成一棵渲染树（包含每个节点的视觉信息）
生成布局（flow），即将所有渲染树的所有节点进行平面合成
将布局绘制（paint）在屏幕上
"生成布局"（flow）和"绘制"（paint）相对更加耗时，合称为"渲染"（render）

// 生成 Style 树
//生成布局树，，then pain
俩中元素 block inline元素。。
每次渲染以一个block元素为基础。。内部调用渲染inline元素。。
坐标系使用top left绝对坐标最简单。。


//----------------------  datarow1-----------
$lastBlockElmt=$row327;

for($i=0;$i<5;$i++)
{
 $row614 = array("top" => $lastBlockElmt['top']+ $lastBlockElmt['height'],"th_row" => "false", "left" => 0, 'bkgrd' => '', "padBtm" => 0,  'font' => $font, 'font_size' => $font_size, 'height' => $css_lineHight);
 $row614["childs"] = [

   array('txt' => "庄".$i, 'ballwidth' => 40, 'color' => "gray", 'shape' => 'ball',  'bkgrd' => "red", 'id' => 'cell1', 'align' => 'left', 'padLeft' => 10, 'width' => 350, 'height' => $css_lineHight),

 ];
 $row614['width']=calcRowWd($row614);
 $GLOBALS['dbg']=1;
 renderElementRowV3($row614, $img, $outputPic);
 $lastBlockElmt=$row614;
}



/**
*
*   //render cell font n th_line need row seting
* @param $v_cell
* @param $img

* @param $outputPic
* @param array $row140
* @return mixed
*/
function renderCell($v_cell, $img,  $outputPic, array $row140) {
 $blktxt = array_key('txt', $v_cell);
 //  if($idx>0)
 //   $posX = $posX + $v_cell['width'];
 $posX=$v_cell['left'];
 $posY=$v_cell['top'];

 imagepng($img, $outputPic);

 if(  $GLOBALS['dbg']==1)
   echo 1;
 //-------------bkgrd ---- imagefilledrectangle

 if (hasAttr('bkgrd', $v_cell)){

   $curClr = getColor($v_cell['bkgrd'], $img);

   if ( Attr('shape', $v_cell)=="ball"){

     $pos_x_eclps = $v_cell['left'] + $v_cell['width'] / 2;
     $pos_y_eclps = $v_cell['top'] + $v_cell['height'] / 2;
     $ballwidth = array_key("ballwidth", $v_cell);
     imagefilledellipse($img, $pos_x_eclps, $pos_y_eclps, $ballwidth, $ballwidth, $curClr);
     renderSmallball($v_cell, $pos_x_eclps, $pos_y_eclps, $ballwidth, $img, $outputPic);

   } else {
     //df rect
     imagefilledrectangle($img, $v_cell['left'],  $v_cell['top'], $posX + $v_cell['width'], $posY + $v_cell['height'], $curClr);

   }

   imagepng($img, $outputPic);
 }


//—-------td txt

 $font_baseline_y = $posY + $row140['height'] - ($row140['height'] - $row140["font_size"]) / 2;

 $font_x = calcFontX($v_cell, $posX, $row140["font_size"]);
 $font = $row140['font'];
 if (!array_key_exists('color', $v_cell))
   $v_cell['color'] = "black";
 imagettftext($img, $row140["font_size"], 0, $font_x, $font_baseline_y, getColor($v_cell['color'], $img), $font, $blktxt);
 imagepng($img, $outputPic);

 //-------------titlew line rit
 if (getCellTagName($v_cell) == "th") {
   //竖线。。。
   //todo th implt
   //if th then pain shuxian
   $line_posx = $posX + $v_cell['width'];

   imageline($img, $line_posx, 0, $line_posx, 2000, getColor("black", $img));
 }
 if (array_key("th_row", $row140) == "true") {
   //竖线。。。
   //todo th implt
   //if th then pain shuxian
   $line_posx = $posX + $v_cell['width'];

   imageline($img, $line_posx, 0, $line_posx, 2000, getColor("black", $img));
 }


 imagepng($img, $outputPic);
 return $v_cell;
}

