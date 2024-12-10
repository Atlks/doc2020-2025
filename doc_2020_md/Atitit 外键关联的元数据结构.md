Atitit 外键关联的元数据结构

REFERENTIAL_CONSTRAINTS
只有 表关系的引用，么空有col   


TABLE_CONSTRAINTS 只有主键 uniq


select * from information_schema.INNODB_SYS_FOREIGN
也是只有表
CREATE TEMPORARY TABLE `INNODB_SYS_FOREIGN` (
  `ID` varchar(193) NOT NULL DEFAULT '',
  `FOR_NAME` varchar(193) NOT NULL DEFAULT '',
  `REF_NAME` varchar(193) NOT NULL DEFAULT '',
  `N_COLS` int(11) unsigned NOT NULL DEFAULT '0',
  `TYPE` int(11) unsigned NOT NULL DEFAULT '0'
) ENGINE=MEMORY DEFAULT CHARSET=utf8;



CREATE TEMPORARY TABLE `INNODB_SYS_FOREIGN_COLS` (
  `ID` varchar(193) NOT NULL DEFAULT '',
  `FOR_COL_NAME` varchar(193) NOT NULL DEFAULT '',
  `REF_COL_NAME` varchar(193) NOT NULL DEFAULT '',
  `POS` int(11) unsigned NOT NULL DEFAULT '0'
) ENGINE=MEMORY DEFAULT CHARSET=utf8;



select * from information_schema.INNODB_SYS_FOREIGN  t LEFT JOIN  information_schema.INNODB_SYS_FOREIGN_COLS  c on t.id=c.id

