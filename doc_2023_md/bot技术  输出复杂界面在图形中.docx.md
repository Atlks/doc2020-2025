bot技术  输出复杂界面在图形中



输出得到文字块  imagettfbbox



  // 画矩形 （先填充一个大背景，小一点的矩形形成外边框）
        imagefill($img, 0, 0, $bg_color);
        imagefilledrectangle



     imageline($img, $x, $title_height, $x, $img_height, $bg_color);
            $pre_col_x[$k] = $x;
            //写入首行 
            imagettftext($img, $font_title_size, 0, $title_x + intval(($col_x + $x_padding * 2 - $pre_title_w[$k]) / 2), intval($title_height - $font_title_size / 2), $title_color, $font, $data[$k]);
    



  // 画线 hengsye
            imageline($img, 0, $temp_height, $img_width, $temp_height, $bg_color);




化圆圈

 imageellipse($image, $pos_x, $pos_y, $elipse_w, $elipse_h, $color);

