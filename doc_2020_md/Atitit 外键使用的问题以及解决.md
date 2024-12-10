Atitit 外键使用的问题以及解决


Cant create fk

ALTER TABLE `football_score_t` ADD CONSTRAINT `比赛关联` FOREIGN KEY (`match_id`) REFERENCES `basketball_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL;

 SET FOREIGN_KEY_CHECKS = 0;
ALTER TABLE `football_score_t` ADD CONSTRAINT `比赛关联` FOREIGN KEY (`match_id`) REFERENCES `basketball_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL;



Tmple insert

外键名字不能重复，哪怕跨表
外键查询
select t.id,t.for_name 子表for_name,c.for_col_name,t.ref_name 父表ref_name,c.ref_col_name from information_schema.INNODB_SYS_FOREIGN  t 
LEFT JOIN  information_schema.INNODB_SYS_FOREIGN_COLS  c on t.id=c.id
where t.id like '%kok%'
order by t.for_name


