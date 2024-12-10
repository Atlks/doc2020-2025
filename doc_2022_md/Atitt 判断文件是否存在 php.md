Atitt 判断文件是否存在 php

    echo $url."\r\n<p>";
    if(@fopen($url, 'r')) {
        echo '文件存在';
    } else {
        echo '文件不存在';
        $sql="delete from mac_vod where vod_id=".$v['vod_id'];
        echo $sql."\r\n<p>";
        pdo_exec($sql);
    }


但如果url 404跳转到首页，则无法判断了。。。




get_headers模式比较准，，，


    $array = get_headers($url,1);
if(preg_match('/200/',$array[0])){
    echo "有效资源<pre/>";
    print_r($array);
}else{
    echo "无效url资源！";
         echo '文件不存在';
        $sql="delete from mac_vod where vod_id=".$v['vod_id'];
        echo $sql."\r\n<p>";
        pdo_exec($sql);
}

