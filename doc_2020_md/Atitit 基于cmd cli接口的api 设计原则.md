Atitit 基于cmd cli接口的api 设计原则

小于7个参数的情况下还是使用args模式为好。
否则使用apache cli吧。。或者system。getProp也可以。。

要考虑cli的回显。。一定要echo..

至于启动参数可以放在注释里面。。
/**
	 * "fixseed" "c:\\0key\\pri.txt"  "c:\\0key\\pub.txt" 
