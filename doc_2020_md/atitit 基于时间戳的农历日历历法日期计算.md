Atitit.基于时间戳的农历日历历法日期计算


1. 农历xx年的大小月份根据万年历查询	1
2. 农历xx年1月1日的时间戳获取	1
3. 计算当年的时间戳与农历日期的对应表，时间戳为key，日期为val	1
4. 根据获取的时间戳得到农历日期	2


农历xx年的大小月份根据万年历查询

2006 年大进的月份13689，11,12
闰月的月份 none
小金月份2457,10

农历xx年1月1日的时间戳获取
农历2016年1月1日，换算为公历的2016-02-08 ，获取时间戳（sec为单位）
2016-02-08 00:00:01的时间戳为：1454860801

// 获取某个时间格式的时间戳
var stringTime = "2016-02-08 00:00:01";
var timestamp2 = Date.parse(new Date(stringTime));
timestamp2 = timestamp2 / 1000;
//2014-07-10 10:21:12的时间戳为：1404958872 
console.log(stringTime + "的时间戳为：" + timestamp2);

精确到天的时间戳 16838.66667824074 天


作者::  ★(attilax)>>>   绰号:老哇的爪子 （ 全名：：Attilax Akbar Al Rapanui 阿提拉克斯 阿克巴 阿尔 拉帕努伊 ） 汉字名：ail，  EMAIL:1466519819@qq.com
转载请注明来源： http://blog.csdn.net/attilax

计算当年的时间戳与农历日期的对应表，时间戳为key，日期为val
 var base=16838;
var lit_a=[2,4,5,7,10];
var map={};
var map_abs={};
var offset=1;
for(var i=1;i<=12;i++)
{
	for(var j=1;j<=30;j++)
	{
		map[offset]=i+"-"+j;
		map_abs[offset+base]=i+"-"+j;
		console.log(" offset:"+offset+"    date:"+map[offset]);
		offset++;
	   if(lit_a.indexOf(i)>-1) //if mon is litt mon
	   {
		   if(j>=29)
			break;
	   }
   }

}

根据获取的时间戳得到农历日期
function getNowDateTmstmp()
{


var timestamp = Date.parse(new Date());
   timestamp=timestamp/(3600*24*1000);
   return Math.floor(timestamp);
}


var nowStmp_date=getNowDateTmstmp();
alert( map_abs[nowStmp_date]);

