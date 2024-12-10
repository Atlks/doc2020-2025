Atitt createroom 创建房屋api

D:\src_nml\live\PhalApi\Appapi\Api\Live.php
        $domain = new Domain_Live();
        $result = $domain->createRoom($uid,$dataroom);


D:\src_nml\live\PhalApi\Appapi\Domain\Live.php
class Domain_Live {
    public function createRoom($uid,$data) {
        $rs = array();

        $model = new Model_Live();
        $rs = $model->createRoom($uid,$data);
        return $rs;
    }



D:\src_nml\live\PhalApi\Appapi\Model\Live.php

class Model_Live extends PhalApi_Model_NotORM {
    /* 创建房间 */
    public function createRoom($uid,$data) {
 /* 加入 */
                $rs=DI()->notorm->live->insert($data);




Di>notRom>live表插入一条记录



CREATE TABLE `cmf_live` (
  `uid` int(20) unsigned NOT NULL DEFAULT '0' COMMENT '用户ID',
  `showid` int(12) NOT NULL DEFAULT '0' COMMENT '直播标识',
  `islive` int(1) NOT NULL DEFAULT '0' COMMENT '直播状态',
  `starttime` int(12) NOT NULL DEFAULT '0' COMMENT '开播时间',
  `title` varchar(255) NOT NULL DEFAULT '' COMMENT '标题',
  `province` varchar(255) NOT NULL DEFAULT '' COMMENT '省份',
  `city` varchar(255) NOT NULL DEFAULT '' COMMENT '城市',
  `stream` varchar(255) NOT NULL DEFAULT '' COMMENT '流名',
  `thumb` varchar(255) NOT NULL DEFAULT '' COMMENT '封面图',
  `pull` varchar(255) NOT NULL DEFAULT '' COMMENT '播流地址',
  `lng` varchar(255) NOT NULL DEFAULT '' COMMENT '经度',
  `lat` varchar(255) NOT NULL DEFAULT '' COMMENT '维度',
  `type` tinyint(1) NOT NULL DEFAULT '0' COMMENT '直播类型',
  `type_val` varchar(255) NOT NULL DEFAULT '' COMMENT '类型值',
  `isvideo` tinyint(1) NOT NULL DEFAULT '0' COMMENT '是否假视频',
  `wy_cid` varchar(255) NOT NULL DEFAULT '' COMMENT '网易房间ID(当不使用网易是默认为空)',
  `goodnum` varchar(255) NOT NULL DEFAULT '0' COMMENT '靓号',
  `anyway` tinyint(1) NOT NULL DEFAULT '1' COMMENT '横竖屏，0表示竖屏，1表示横屏',
  `liveclassid` int(11) NOT NULL DEFAULT '0' COMMENT '直播分类ID',
  `hotvotes` int(11) NOT NULL DEFAULT '0' COMMENT '热门礼物总额',
  `pkuid` int(11) NOT NULL DEFAULT '0' COMMENT 'PK对方ID',
  `pkstream` varchar(255) NOT NULL DEFAULT '' COMMENT 'pk对方的流名',
  `ismic` tinyint(1) NOT NULL DEFAULT '0' COMMENT '连麦开关，0是关，1是开',
  `ishot` tinyint(1) NOT NULL DEFAULT '0' COMMENT '是否热门',
  `isrecommend` tinyint(1) NOT NULL DEFAULT '0' COMMENT '是否推荐',
  `deviceinfo` varchar(255) NOT NULL DEFAULT '' COMMENT '设备信息',
  `isshop` tinyint(1) NOT NULL DEFAULT '0' COMMENT '是否开启店铺',
  `game_action` tinyint(1) NOT NULL DEFAULT '0' COMMENT '游戏类型',
  `banker_coin` bigint(20) DEFAULT '0' COMMENT '庄家余额',
  `isoff` tinyint(1) NOT NULL DEFAULT '0' COMMENT '是否断流，0否1是',
  `offtime` bigint(20) NOT NULL DEFAULT '0' COMMENT '断流时间',
  `recommend_time` int(1) NOT NULL DEFAULT '0' COMMENT '推荐时间',
  `live_link` varchar(255) DEFAULT '' COMMENT '广告链接',
  PRIMARY KEY (`uid`),
  KEY `index_islive_starttime` (`islive`,`starttime`) USING BTREE,
  KEY `index_uid_stream` (`uid`,`stream`) USING BTREE
