Atitit 时间的展示格式与存储格式


赛事时间的格式起源
在公元前8000年至前3500年间，苏美尔人发明了使用粘土保留数字信息。他们的做法是将各种形状的小的粘土记号像珠子一样串在一起。从大约前3500年开始，粘土记号逐渐被数字符号取代。这些数字符号是使用圆的笔针刻在粘土块上，然后烧制而成的。大约前3100年，数字符号与被计数的事物分离，成为抽象的符号。在前2700年至前2000年间，圆的笔针逐渐被一种尖的笔针取代，这种笔针可以在粘土上刻出楔形符号。这种楔形数字和圆形数字相似，并保留了符号数值记数法。这些记数系统逐渐演变成了一种常见的六十进制系统。这个系统是一种位置数值记数法，只使用竖向的楔形和人形两种符号，而且能够表示分数。这个系统在古巴比伦的初期（大约前1950年）得到了充分的发展，并成为巴比伦尼亚的标准。
上述六十进制系统是一种混合进位制系统，它的一个符号序列的不同位置上使用10和6两个基数。这个系统被广泛地应用于商业，同时也在天文学和其他计算中被使用。这个系统从巴比伦尼亚输出，并传遍了美索不达米亚，包括希腊，罗马和埃及。今天，我们仍然用它来计算时间（1小时=60分钟）和角度（1度=60分）。
六十[编辑]
基数为60的系统（六十进制）是苏美尔人和他们在美索不达米亚的继承者所使用的，今天还在我们的计时系统中存在（所以一小时有60分钟而一分钟有60秒）。60也有大量因子，包括前六个自然数。六十进制系统被认为是因为十进制和十二进制合并过程中产生的。中国历法中，六十进制的甲子系统用于表示年，12个动物的生肖系统对应。


1h 12m 23s 模式 （可读性最好
日常模式 1：45：44
持续时间格式  小时h分‘秒’毫秒（双位）

它不是特别常见的时间表达。该'和"被广泛应用于地图。 也用来指示时间的持续计时
它类似于度-分-秒：而不是十进制度（38.897212°，-77.036519°）而是写（38°53′49.9632″，-77°2′11.4678″）。两者均源自六分法计数系统，例如古代巴比伦（Ancient Babylon）中设计的系统：单素数代表第一个六分法划分，第二个代表第二个六分法划分，依此类推。17世纪的天文学家使用三分之一的1/60分之一秒进行划分。
使用分钟和秒符号表示时间的优势在于它显然表示持续时间而不是时间。
从时间01:00:00到时间02:34:56的持续时间为1小时34分56秒（1h 34′56”）
质数标记以单数开头，并相乘以用于后续出现，因此分钟使用单质数'，秒使用双质数'。在这种持续时间的情况下，它们分别发音为分钟和秒。
请注意，素数'不是直撇号'或打印机的'撇号'，尽管直撇号是一个合理的近似值，并且打印机的撇号也会出现。



时间的写法中例如 ： 1'56''27 ,我想问的是双引号后面的时间单位是毫秒吗，也就是1分56秒27毫秒
1秒＝1000毫秒，那么如果毫秒上百的话，比如1分56秒300毫秒，岂不是要写成1'56''300，可是我从来没见过双引号后面写三位的啊，都是写两位的，谁知道，这是为什么，是不是我理解错了
秒后面的单位是 1/100秒 而不是毫秒 （1秒=1000毫秒），因为出于格式的统一，计时器一般是xx分xx秒xx的格式 最后是没有单位的。但是最后一个数大家在生活中会习惯性喊做 毫秒，其实是不对的。一般奥运会之类的就会这么说，12秒88 不会说后面是什么单位

比赛时间转换秒数

import java.time.Duration;
import java.util.HashMap;
import java.util.Map;

public class Timeutil {
	 
	public static void main(String[] args) {
		String time="2'1''55";
		 time="61'";
		 
		System.out.println(toSecs(time));
	}

	public static long toSecs(String time) {
		
		//convert hsm mode
		time=time.replaceAll("''", "S");
		time=time.replaceAll("'", "M");
		String t=time;
	    //
		Map m=new HashMap() {{ // parse time str fmt 
			int indexOfMill = t.indexOf("S");
			String timeNoMillsec=t.substring(0,indexOfMill+1);	
			if(indexOfMill==-1) //excpt
				timeNoMillsec=t;
			put("timeNoMillsec",timeNoMillsec);
			String mill=t.substring(indexOfMill+1);
			put("mill",timeNoMillsec);
			
		}};
	
		String timeNoMillsec="PT"+m.get("timeNoMillsec").toString();
		System.out.println(timeNoMillsec);
		//"P1DT1H10M10.5S"
		Duration fromChar1 = Duration.parse(timeNoMillsec);
		
		//process millsec
		try {
			
			fromChar1.plusMillis(Long.parseLong(m.get("mill").toString()));
		} catch (Exception e) {
			System.out.println(e);
		}
		
	 
		return fromChar1.getSeconds();
	}

}

规范与标准
1995年颁布的《出版物上数字用法的规 定》对此问题有明确的说明：“用扩展格式表 示时间，时、分、秒之间应该用冒号。

ISO 8601 - 维基百科，自由的百科全书
