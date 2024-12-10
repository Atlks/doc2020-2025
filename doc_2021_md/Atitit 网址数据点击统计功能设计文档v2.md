Atitit 网址数据点击统计功能设计文档



MODIFY COLUMN `website_hits` mediumint UNSIGNED NOT NULL DEFAULT 0 COMMENT 'totalclick' AFTER `website_time_make`,
MODIFY COLUMN `website_hits_day` mediumint UNSIGNED NOT NULL DEFAULT 0 COMMENT 'yarclick' AFTER `website_hits`;

功能要点概述

配置url和图片，后前端展示一个幻灯片切换，点击后调转，顺便统计点击数据

增加条增加访问记录，用来进来昨日点击统计使用。

	后端配置界面
http://localhost:63342/nzsp1_cms/application/admin/view/website/index.html?_ijt=ou5k89ekcd7taoh5t1p86q6ajf
<th width="50">编号</th>
<th >名称</th>
<th width="350">网址</th>
<th width="50">总点击</th>
<th width="50">昨日点击</th>
<th width="50">来路</th>
<th width="30">推荐</th>
<th width="30">浏览</th>
<th width="120">更新时间</th>
<th width="170">操作</th>




前端界面 id713

 <!-- url data mode -->
   <script >
       function goto77(url){
           url77='/util/clickStats.php?url='+encodeURIComponent(url);
           open(url77)
       }
   </script>

   <!-- id713  jeig sh index use..  -->
<div role="listbox" class="carousel-inner">
    {maccms:website order="desc"  by="website_hits"  num="10"}
    <div class="item {if condition='$key eq 1'} active {/if}">
        <a href="javascript:goto77('{$vo.website_jumpurl}')"><img src="{:mac_url_img($vo.website_logo)}"
                                             data-holder-rendered="true"/></a>
    </div>
    {/maccms:website}
</div>

表格 mac_website  mac_wbst_clk


Ref

Atitit 网址数据点击统计功能修复总结

