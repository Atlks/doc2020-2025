Atitit 网址数据点击统计功能修复总结


总点击的修复
前端是个幻灯切换也。。让其使用js打开统计php中转页，再转向即可。。。

<!-- url data mode -->
<script >
    function goto77(url){
        url77='/util/clickStats.php?url='+encodeURIComponent(url);
        open(url77)
    }
</script>
<div role="listbox" class="carousel-inner">
    {maccms:website order="desc"  by="website_hits"  num="10"}
    <div class="item {if condition='$key eq 1'} active {/if}">
        <a href="javascript:goto77('{$vo.website_jumpurl}')"><img src="{:mac_url_img($vo.website_logo)}"
                                             data-holder-rendered="true"/></a>
    </div>
    {/maccms:website}
</div>
主要执行俩条sql一条更新总点击数，一条增加访问记录，用来进来昨日点击统计使用。。
$sql="update mac_website set website_hits=website_hits+1 where website_jumpurl='$url_sqlPrm'";

$sql="insert mac_wbst_clk  set dt=now() , url='$url_sqlPrm'";

昨日统计修复

访问地址
http://localhost:81/admin21hxc.php/admin/website/data.html

Tp5日志位置 runtime、log查看日志，得到control地址以及view地址
--------------------------------------------------------------
[ 2021-07-17T01:10:06+08:00 ] 127.0.0.1 GET localhost:81/admin21hxc.php/admin/website/data.html
info ] [ BEHAVIOR ] Run app\common\behavior\Begin @app_begin [ RunTime:0.000842s ]
[ info ] [ DB ] INIT mysql
[ info ] [ RUN ] app\admin\controller\Website->data[ C:\wamp\www\nzsp1_cms\application\admin\controller\Website.php ]
[ info ] [ CACHE ] INIT file
[ info ] [ VIEW ] C:\wamp\www\nzsp1_cms/application/admin\view\website\index.html [ array (



Tp5模板语法for循环麻烦的。。直接修改后端php  for循环


Atitit 循环中调用函数解决方法

直接调用函数最简单。。

但如果mvc框架比如tp5 可能麻烦些。。

此时可以预先在里面循环，调用，把值写入list再输出裂表。。。

这样前端for 就可以不用动，更加普世。。。


因为tp5 和php都是for，，但php更加通用些啊。。。


global  $pdo;
require __DIR__."/../../../conn.php";

var_dump_ati($pdo);
error_log('$pdo cur is ::');
error_log($pdo);
foreach($res['list'] as $k=>&$v){
    $v['ismake'] = 1;
    if($GLOBALS['config']['view']['website_detail'] >0 && $v['website_time_make'] < $v['website_time']){
        $v['ismake'] = 0;
    }
    $v['website_hits_day']=99;
    $url= $v['website_jumpurl'];
    $sql="  select count(1) from mac_wbst_clk  where dt=date_sub(curdate(), interval 1 day) and url='$url'";
    error_log($sql);
    $v['website_hits_day']=  fetchColumnVal($sql);

}


