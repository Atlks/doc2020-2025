Atitit mysql statu parse 表格统计分析数据


找到体积占有最大的表

select table_name,table_rows,data_length,data_length/1000000 from  information_schema.tables where table_schema='eladmin' order by data_length desc
events_list
