Nodejs 最佳实践 bp zjsj



Dev tool env 
增加jsodc类型提示    1. 类型检查机制
注意查看prblm ide 改善代码可靠性
利用jsdopc根据实现增强api可读性和可靠性
Dev method  fp

开发工具都不能为JS提供足够好的智能提示
使用简单函数即可，不要oo 这样方便ide提示
查看次语言的bug和要避免的坑
模块使用cjs语法，方便兼容
主题 可以使用mjs方便await调用直接使用
尽可能采用同步接口方便理解
File读取同步
http get同步模式 node-fetch  sync-request

import fetch from "node-fetch"; 
这俩哥都很简单。

Db同步



注意兼容await 同步  循环要用for 不要foreach


Ex catch  set all glb ex cathr  n log
. Release resouce juse use exec


Php dev bp zjsj 

