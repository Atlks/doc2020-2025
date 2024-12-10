Atitit 单独测试mybatis缓存的效果对比

20thrd use save map


20thd use web test   3s  2s

j":null,"total":0,"recordsTotal":0,"recordsFiltered":0,"rows":[],"data":null,"tableField":null}
2018-04-18 20:03:14,872 INFO [test.copy2.Mythread_web] - <----------------------------------------------Mythread_web threadnum:6，耗时：2929豪秒------------------------------------------------------>
**************************************{"result":"Success","resultMsg":"","list":[{"vaf01":"959001344616697859"}],"map":null,"obj":null,"total":0,"recordsTotal":0,"recordsFiltered":0,"rows":[],"data":null,"tableField":null}
2018-04-18 20:03:14,875 INFO [test.copy2.Mythread_web] - <----------------------------------------------Mythread_web threadnum:17，耗时：2930豪秒-


20thd webtest use mybatis cache

50thd 4s 6666豪秒  4s

Mybatis cache
50thd  4.5s   3.9s   4.3s  4.3s

6.5s when redis cache



