Atitit mysql查询缓存分析与优化计划

（貌似不能缓存，开奖号码来源于实时查询）开奖号码表 缓存最近几天的 sSC_dATA WHERE NUMBER = ? AND  PLAY_gROUP_iD = ?    


FROM cOMPANY WHERE ( IS_eNABLE = ? )    公司表可以缓存 
 
sSC_pLAY   玩法，千条记录 可以缓存
ssc_play_group   彩种  32条记录
ssc_play_pl   玩法赔率  1w1千多条

天天分钱表  可能也能缓存  dD_cENTS WHERE ( ORDER_nUMBER = ? and CENTS_sTATUS = ? )  


Atitit 开奖sql日志记录
