
PHP 三种方式实现链式操作


 方法一、使用魔法函数__call结合call_user_func来实现
调用函数的方法 call_user_func_array($function, [$arg1, $arg2])
方法二、使用魔法函数__call结合call_user_func_array来实现
<?php

class StringHelper {
    private $value;
    
    function __construct($value)
    {
        $this->value = $value;
    }

    function __call($function, $args){
        array_unshift($args, $this->value);
        $this->value = call_user_func_array($function, $args);
        return $this;
    }

    function strlen() {
        return strlen($this->value);
    }
}
$str = new StringHelper("  sd f  0");echo $str->trim('0')->strlen();
说明：
array_unshift(array,value1,value2,value3...)
array_unshift() 函数用于向数组插入新元素。新数组的值将被插入到数组的开头。
call_user_func()和call_user_func_array都是动态调用函数的方法，区别在于参数的传递方式不同。
方法三、麻烦 不使用魔法函数__call来实现  修改_call()为trim()函数
只需要修改_call()为trim()函数即可：
public function trim($t){
    $this->value = trim($this->value, $t);
    return $this;
}
重点在于，返回$this指针，方便调用后者函数。
php
赞9收藏10
分享
阅读 7.6k发布于 2017-01-18





在路上

531 声望25 粉丝
关注作者

下一篇 »
MYSQL 使用show profiles 分析性能
引用和评论
被 1 篇内容引用



为什么类可以用->一次性调用多个方法

推荐阅读


使用Guava RateLimiter限流以及源码解析
在路上赞 2阅读 7.1k评论 1


通过小程序实现微信扫码登录，个人网站接入微信扫码登录功能
TANKING赞 5阅读 5.6k评论 3


docker 学习笔记
hufeng赞 1阅读 2.9k


一个非常实用的php数据库pdo操作类（curd操作类）
TANKING赞 2阅读 3.1k评论 1


悬赏任务源码+开源威客系统网站源码+部署教程
火爆的筷子赞 1阅读 4.4k评论 1


静态编译swoole-cli并调用rust的动态链接库
vanve赞 3阅读 981评论 2


〔抽奖揭秘〕为啥年会你抽不到特等奖
极客飞兔赞 2阅读 783评论 2

2 条评论
得票最新


提交评论
评论支持部分 Markdown 语法：**粗体** _斜体_ [链接](http://example.com) `代码` - 列表 > 引用。你还可以使用 @ 来通知其他用户。

zshanjun：
nice，最后一种最简单
回复2017-03-23

冯小贤：
不错
回复2018-02-02
©2023 Kevin的编程之路
除特别声明外，作品采用《署名-非商业性使用-禁止演绎 4.0 国际》进行许可
使用 SegmentFault 发布
SegmentFault - 凝聚集体智慧，推动技术进步
服务协议隐私政策浙ICP备15005796号-2浙公网安备33010602002000号

