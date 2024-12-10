
Atitit bootsAtitit bootstrap布局 栅格.docx
trap布局 栅格
<div class="video-wrapper container-fluid row" id="targetDiv" >
<!-- per video-->
<div v-for="item in items" class="col-style   lazy loaded col-md-3">
    </div>


<!-- per video  end -->


简述container与container-fluid的区别
bootstrap
 阅读约 2 分钟
在bootstrap中的布局容器一栏中，提供了container与container-fluid两种容器，其官方解释为：
.container 类用于固定宽度并支持响应式布局的容器。
.container-fluid 类用于 100% 宽度，占据全部视口（viewport）的容器。
所以，先说一说它们的共同点：这两种容器的高度设定都是一致的，都为auto。而他们的不同就在于它们宽度的设定上。

container根据屏幕宽度利用媒体查询，已经设定了固定的宽度，作用为阶段性的改变宽度，所以在改变浏览器的大小时，页面是一个阶段一个阶段变化的。


container-fluid则是将宽度设定为auto，所以当缩放浏览器时，它会保持全屏大小，始终保持100%的宽度。



栅格系统
Bootstrap 提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多12列。它包含了易于使用的预定义类，还有强大的mixin 用于生成更具语义的布局。



Bootstrap 包含了一个响应式的、移动设备优先的、不固定的网格系统，可以随着设备或视口大小的增加而适当地扩展到 12 列。

它包含了用于简单的布局选项的预定义类，也包含了用于生成更多语义布局的功能强大的混合类。

2等分  要3等分 4等分 中等屏幕
如果要2等分，使用col-md-6即可；要3等分，使用col-md-4即可；但如果我们要5等分或者8等分怎么办呢？下面的示例是bootstrap五等分布局：
默认pc屏幕，如果手机显示则自动竖排显示。。
————————————————
实例：从堆叠到水平排列
使用单一的一组 .col-md-* 栅格类，就可以创建一个基本的栅格系统，在手机和平板设备上一开始是堆叠在一起的（超小屏幕到小屏幕这一范围），在桌面（中等）屏幕设备上变为水平排列。所有“列（column）必须放在 ” .row 内。
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-1
.col-md-8
.col-md-4
.col-md-4
.col-md-4
.col-md-4
.col-md-6
.col-md-6

专门调整手机下的显示格子 超小屏幕 手机 (<768px) .col-xs-
排版模式
手机优先，电脑下同样扩大（推荐），设置col-xs-6
Ex small   。。手机信息度秘笈比较大。但是如果很小的手机，会出现横行滚动条。。pc上可能会浪费空间，太空阔
   <DIV class=".container-fluid">
            <div class="row">
                <div class="col-xs-6 col-md-3xx ">

Pc优先，手机下自动流逝布局设置md模式
Pc手机分别设置，分别设置xs md模式
Other
分别正对手机 电脑 排版布局 列宽度





中等屏幕 桌面显示器 (≥992px) .col-md-

如果只设置pc,,then if on cp view...auto flow mode...
