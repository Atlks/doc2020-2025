Atitt 设计文档整理 猜你喜欢也许你会喜欢功能

Freeplay
Play。Html

界面已经改为vue实现了。

<div class="video-wrapper container-fluid row" id="targetDiv">
    <div id="comLoader" class="loader" style="display: none;">
        <div class="loader-inner ball-beat">
            <div></div>
            <div></div>
            <div></div>
        </div>
    </div>

    <!-- per video freeplay page-->
    <div v-for="item in items" class="col-style   lazy loaded col-md-3"
         style="height: 250px !important;">
        <a v-bind:href="item.linkHref" target="_blank" class="videoBox">
            <div class="videoBox_wrap">
                <div class="videoBox-cover"
                     v-bind:style="{backgroundImage:'url(' + item.vod_pic_urlImg + ')'  }"></div>
            </div>
            <div class="videoBox-info">
                <span class="title"
                      style="font-size: 13px;color: #0C0C0C;"> {{ item.vod_name }}  </span>
            </div>
            <div class="videoBox-action">
                <span class="views"><i class="fa fa-eye"></i><span class="number"
                                                                   style="line-height: 20px;">{{ item.vod_hits}}</span></span>
                <span class="likes"><i class="fa fa-heart"></i><span class="number"
                                                                     style="line-height: 20px;">{{ item.vod_up}} </span></span>
            </div>
        </a>
    </div>


    <!-- per video  end -->



C:\wamp\www\nzsp1_cms\rpt\vodList_GuessFav.php

<?php
//   /rpt/vodList_GuessFav.php?
header('Access-Control-Allow-Origin:*');

require "../conn.php";
require "../application/common.php";

$sql="
select  type_id  from mac_type order by   rand()  limit 1;
-- select @tpid;



";
$typd_id=fetchColumnVal($sql);
//  -- select * from mac_vod order by   rand()   limit 20
echo $sql."\n";

$sql=" select * from mac_vod  where type_id = ($typd_id) limit 20 ";  echo $sql."\n";
$rows = queryPdo($sql, $pdo);
foreach($rows as $k => &$v){
  // echo $k.":".$v."\r\n";   //   0:Array
    $v['vod_pic_urlImg']=mac_url_img( $v['vod_pic']);
    $vodid= $v['vod_id'];
    $v['linkHref']= "/index.php/vod/play/id/$vodid/sid/1/nid/1.html";

 //  global  $rows;
 //   　　$rows[$k] = 1;

}

//mac_url_img($vo.vod_pic)

 echo PHP_EOL.'-----------------attilax---'.PHP_EOL;
echo json_encode($rows);

