Atitit 分析问题与复现bug


Bug复现
多线程环境调用单元测试
增加sleep，模拟压力大时延迟增加
有时候bug自然触发的概率很低，需要用一些人为的手段来帮助触发（比如故意在某个原本比较快的过程中增加sleep，模拟压力大时延迟增加的现象），需要增加一些额外的代码

