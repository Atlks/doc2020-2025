Atitit 税率计算说明 #sale #tax

最新源码 
C:\Users\ATI\Documents\sumdoc u3sfx homepc u314\saletax.zip

/**v5 x修正格式化问题
 * encode ：：utf8 auto；；attilax v5 可读性增强 增加注释 v4增加可读性
 * 
 * 
 */
/*
 * 计算税率主要思路流程：：
 * 1. 内存数据表LIST 进行投影运算 循环 获取税率，UDF计算单项税金，
 * 2. 聚合运算 计算总税
 * 2. 格式化展示
 * 
 * */


