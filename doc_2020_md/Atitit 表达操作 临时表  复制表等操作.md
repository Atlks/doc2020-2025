Atitit 表达操作 临时表  复制表等操作


CREATE TABLE tmp_data SELECT * FROM football_score_t;



INSERT IGNORE INTO football_score_t SELECT * from tmp_data;


忽略约束插入数据 复制数据
 SET FOREIGN_KEY_CHECKS = 0;
INSERT IGNORE INTO football_score_t SELECT * from tmp_data;
