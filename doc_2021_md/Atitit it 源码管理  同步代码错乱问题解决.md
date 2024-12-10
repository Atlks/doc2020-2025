Atitit it 源码管理  同步代码错乱问题解决


不要格式化代码

重新启用一个方法。方便切换 和源码对比
原来方法如果改变很大，那么
。。改变调用者即可。。

把原来方法增加dep标注


注释掉原来对行，而不是取代
//	this.querySettle();
				this.querySettleV2();
