Atitit MP3元数据抽取结果 音乐信息检索

取出了重复和英文的数据  一共368个。。

/bookmarksHtmlEverythingIndexPrj/src/apkg/songlistCnDeduliCsv.java
ackage apkg;

import java.io.File;
import java.io.IOException;
import java.util.Set;

import org.apache.commons.io.FileUtils;

import com.alibaba.fastjson.JSONArray;
import com.alibaba.fastjson.JSONObject;
import com.google.common.collect.Sets;

public class songlistCnDeduliCsv {

	public static void main(String[] args) throws IOException {
		Set<String> st=Sets.newConcurrentHashSet();
		File file = new File("d:\\MusicMetaJsonList.txt");
		JSONArray  ja=JSONArray.parseArray(FileUtils.readFileToString(file,"gbk"));
		for (Object object : ja) {
			JSONObject jo=(JSONObject) object;
			String string = jo.getString("SongName")+","+jo.getString("Artist")+","+jo.getString("Album");
			st.add(string);
			
		}
	 System.out.println(st.size());
		
		for (String s : st) {
			if(s.trim().length()>0)
			{
				char c=s.charAt(0);
				int i=c;
				if(c>255 || c<0) //online hezi
				System.out.println(s);
			}
			
		}

	}

851
火苗,格格,
水边的阿狄丽娜 (Live),Richard Clayderman,理查德·克莱德曼钢琴曲全集-精?
回心转意,黑龙,回心转意
快乐宝贝,青春美少女,I Miss You
时光海湾,梦然,
美丽的因太克,新疆美丽公主组合,欢乐地跳吧
想起,韩雪,飘雪
东南西北风,卓依婷,蜕变4 婷不了的爱
梁山伯与祝英台,Richard Clayderman,梁祝新感觉
漂亮的姑娘就要嫁人啦,龙猫组合,慢摇串烧之裸婚时代
全是爱,凤凰传奇,最炫民族风
沈念 - 让全世界知道我爱你DJ版,沈念,全部都给你
练习,刘德华,
离别,阿杜,天黑
长相依,卓依婷,化蝶
因为爱着你,龙梅子,因为爱着你
好一朵茉莉花,黑鸭子,影视经典精装版
採槟榔,高胜美,山地情歌2 [雷射金曲10]
红尘情歌 (DJ版),DJ何鹏,DJ何鹏舞曲精选集（三）
青青河边草,高胜美,流金十载
你不离我不弃,天籁天,你不离我不弃
ひとり上手 (漫步人生路) (日语),中島みゆき (中岛美雪),亚洲音乐杂辑
怎样,戴佩妮,
蝶儿蝶儿满天飞,高胜美,流金十载
一生有你,水木年华,青春正传
阳光总在风雨后,许美静,都是夜归人
让泪化作相思雨,黑鸭子,男女情歌对唱
拥抱你离去,张北北,
像风一样自由,许巍,在路上…
真的好想你,龚玥,金牌女声
热情沙漠 (Live),Reborn 双鱼座,超级女声杭州唱区
谁明浪子心,王杰,谁明浪子心
那些花儿,朴树,我心飞翔 电影原声带
老人与海,海鸣威,Dance Dance Dance
掌声响起来,黑鸭子,黑鸭子15周年24K德国HD金蝶 DISC
至少还有你,Super Junior-M,迷 (Me)
感动天感动地,宇桐非,
酒干倘卖无,苏芮,搭错车 电影原声大碟
迟来的爱,黑鸭子,男女情歌对唱
罗密欧与朱丽叶 (钢琴曲),Richard Clayderman,理查德.克莱德曼钢琴曲精选
伤心的人越来越多 (DJ版),DJ,DJ舞曲(华语)系列5
一生爱你千百回,梅艳芳,女人花
小草,杨烁,杨烁儿歌集
我是不是你最疼爱的人,黑鸭子,黑鸭子典盛集6
羞答答的玫瑰静悄悄地开,孟庭苇,谁的眼泪在飞
你是我的玫瑰花,龚玥,流行红
我想有个家,潘美辰,是你
爸爸妈妈,王蓉,多爱
火火的姑娘,东方红艳,火火的姑娘
最熟悉的陌生人,萧亚轩,萧亚轩 同名专辑
梁祝,Richard Clayderman,MEMORIAL CLASSICS
漫步人生路,龚玥,极致女声 情歌测试
最浪漫的事,邝美云,我和春天有个约会
小酒窝 (国语),林俊杰,JJ陆
红尘情歌,郑源,红尘情歌
没有你以后,马博,
白狐,陈瑞,风华绝代
春天里,汪峰,信仰在空中飘扬
等一分钟,徐誉滕,音你而红(60周年群星新歌+精选)
捉泥鳅,张清芳,民歌专辑-留声
我在那一角落患过伤风,冯曦妤,A Little Love
错错错,六哲,被伤过的心还可以爱谁
空の镜,松隆子,footsteps
温柔乡,陈雅森,温柔乡
童话,光良,童话
你会爱我到什么时候,陶钰玉,其实我们都寂寞
双截棍,周杰伦,范特西
最幸福的人,曾春年,
心痛到什么时候 (DJ阿远 Remix),龙梅子,情歌继续唱
我们的爱,飞儿乐团,F.I.R.飞儿乐团
我们的时光,TFBOYS,我们的时光
你潇洒我漂亮,韩宝仪,台湾福建 畅销金曲沙龙镭射效果?
你的过去我不介意,唐古,你的过去我不介意
无地自容,黑豹乐队,黑豹 同名专辑
情歌继续唱 (DJ阿远 Remix),龙梅子,情歌继续唱
寂寞的人伤心的歌,龙梅子,寂寞的人伤心的歌
在心里从此永远有个你 (对唱版),高安,高安原唱精选集
飞蛾扑火,彭丽丽,飞蛾扑火(2011版)
套马杆,乌兰托娅,我要去西藏
小薇,黄品源,
曾经的你,许巍,每一刻都是崭新的
她说,林俊杰,她说 概念自选辑
千千阙歌,陈慧娴,永远是你的朋友
潇洒走一回,叶倩文,潇洒走一回
花花宇宙,陈慧琳,花花宇宙
最爱的人伤我最深,张惠妹,2张皇牌精选辑
未来へ (向着未来),Kiroro,子供といっしょにききたいキロロ
小三 (DJ版),冷漠,造物弄人
爱如星火 (DJ版),DJ何鹏,DJ何鹏舞曲精选集(七)
柔柔的眼波柔柔的你 (DJ何鹏版),星月组合,柔柔的眼波柔柔的你
情人,DJ小可,最新汽车升级版8 滚蛋瞌睡虫
隐形的翅膀,龚玥,流行红
爱情里没有谁对谁错,郑源,源情歌
海边的祈祷,Richard Clayderman,理查德·克莱德曼钢琴曲全集-星?
五哥放养,龚玥,西部情歌
大梦想家,TFBOYS,大梦想家
情一动心就痛,海生,情一动心就痛
今天你要嫁给我,蔡依林,唯舞独尊 演唱会鲜听版&混音
一千零一个愿望 (单人版),杨丞琳,一千零一个愿望（单人版）
你是我红尘中最美的缘,星月组合,你是我红尘中最美的缘
潮湿的心,龚玥,靓声歌后
土耳其进行曲,Richard Clayderman,理查钢琴王子3
天使的翅膀,徐誉滕,李雷和韩梅梅
快乐阿拉蕾 (Remix),DJ小可,最新汽车升级版1 - 车载低音炮
类似爱情,林一杰,你是男的我也爱 电影原声带
大海,张雨生,大海
花好月圆,龚玥,中国年·2012贺年心曲
离别的眼泪 (DJ阿远 Remix),龙梅子,情歌继续唱
有个傻瓜爱过你,唐古,有个傻瓜爱过你
圣诞快乐,T.R.Y,圣诞快乐
爱的供养,杨幂,亲幂关系
平凡之路 (舒缓版),打扰一下乐团,
多情人把灵魂都给了谁,李翊君,醇经典
相见恨晚,彭佳慧,
不得不爱,弦子,首张同名专辑
一瞬间,丽江小倩,在线热搜（华语）系列45
许多年以后 (DJ版),DJ 阿圣,DJ阿圣舞曲精选集（三）
黄昏,周传雄,忘记
一生中最爱,谭咏麟,神话1991
我是不是你最疼爱的人 (DJ 大禹,DJ,
有些人爱着爱着就没了,雪无影,有些人爱着爱着就没了
被伤过的心还可以爱谁,六哲,被伤过的心还可以爱谁
狗尾草 (DJ Sevi),DJ,DJ舞曲(华语)系列6
火火的爱 (DJ何鹏),蓝琪儿,时尚DJ舞曲
你是我心内的一首歌,王力宏,改变自己
凡人歌,李宗盛,李宗盛 (与他们) 的凡人歌
微微一笑很倾城,杨洋,微微一笑很倾城 电视剧原声带
星语心愿,张柏芝,任何天气
妹妹的眼睛会放电,天籁天,其实我不想认输
死心塌地,夹子道,死心塌地
情路弯弯,龙梅子,情歌继续唱
预谋,许佳慧,一拍两散
剑心,张杰,古剑奇谭 电视剧原声带
有多少爱可以重来,迪克牛仔,
恋曲1990,高胜美,经典金选1
我的情深你若懂 (DJ版),DJ何鹏,DJ何鹏舞曲精选集（六）
深情,,
擦肩而过,宇桐非,与你同飞
归来吧,陈慧娴,归来吧
月亮之上,凤凰传奇,月亮之上
很爱很爱你,刘若英,很爱很爱你
不得不爱,潘玮柏,高手
摩天轮,罗百吉,舞懈可击
我的未来不是梦,张雨生,自由歌
小婚礼,吴建豪,Different Man
你是我的糖,金莎,你是我的糖
你知道我在等你吗,迪克牛仔,传奇
夜空中最亮的星,逃跑计划,
我是不是该安静的走开,黎明,4 In Love
蒙娜丽莎的眼泪,林志炫,蒙娜丽莎的眼泪
我的爱情不见了 (对唱版),兰雨,我的爱情不见了
藕断丝连,龚玥,人声典范
城里的月光,许美静,遗憾
犯贱,徐良,犯贱
爱情主演,莫露露,爱情主演
粉红色的回忆,韩宝仪,粉红色的回忆
大城小爱 (Live),王力宏,2006 王力宏盖世英雄Live Concer
一生何求,陈百强,一生何求
爱情伤了你爱情害了我,大庆小芳,爱情伤了你爱情害了我
征服,杨宗纬,
卡农,Richard Clayderman,理查钢琴王子·水晶钢琴梦幻情语
追梦人,阿木,
大城小爱,王力宏,盖世英雄
继续-给十五岁的自己,刘若英,在一起
第一次爱的人,王心凌,爱你
欢快,,
下辈子做你的女人,龙梅子,
月满西楼,龚玥,金装小月
柔柔的眼波柔柔的你,星月组合,柔柔的眼波柔柔的你
咱们结婚吧 (DJ版),DJ威威,中文舞曲(2013)系列03
明天会更好,卓依婷,校园青春乐2
问,梁静茹,
不要在我的伤口撒盐 (DJ版),DJ 阿圣,DJ阿圣舞曲精选集（二）
夜色 (DJ版),DJ 阿圣,DJ阿圣舞曲精选集（四）
春泥,庾澄庆,哈林天堂
约定,周蕙,
天天都想���到你,龚玥,全年伤感歌曲大盘点2
信天游,龚玥,70恋歌
山沟沟,龚玥,西部情歌
你是我红尘中最美的缘 (DJ版),DJ何鹏,DJ何鹏舞曲精选集（六）
走过咖啡屋,黑鸭子,流行的经典
两个人的回忆一个人过,庄心妍,好可惜
羞答答的玫瑰静悄悄的开,黑鸭子,岁月如歌8
梦中的鸟,Richard Clayderman,理查德·克莱德曼钢琴曲全集-星?
爱火 (DJ版),DJ何鹏,DJ何鹏舞曲精选集（四）
你那么爱她,李圣杰,关于你的歌
伤心的人唱着寂寞的歌,马建军,伤心的人唱着寂寞的歌
我热爱的故乡,龚玥,西部情歌
多情的月光,正月十五,小可乐
深夜地下铁,T.R.Y,超人气女组合CD3
嘟比嘟,DJ小可,最新汽车升级版1 - 车载低音炮
追梦人 (Live),田馥甄,梦想的声音 第12期
白狐,陈瑞,白狐 EP
萍聚,李翊君,萍聚 / 珍重·再见
分开旅行,刘若英,我的失败与伟大 2nd Version
我爱你胜过你爱我,冷漠,冷漠经典对唱情歌
感恩的心,杨烁,杨烁儿歌集
狗尾草,安旭,
不爱又何必纠缠,吉佑社,毕业那天我们一起失恋
把悲伤留给自己 (Live),辛龙,梦想星搭档 第6期
默,那英,
爱你一万年,刘德华,Melody Andy
爱如星火,冷漠,叹红颜
舞女泪,韩宝仪,台湾福建 畅销金曲沙龙镭射效果?
泡沫,G.E.M. 邓紫棋,
难得有情人,关淑怡,宝丽金难忘的回忆精选Ⅲ
今天你要嫁给我,陶喆,太美丽
爱的忏悔 (DJ版),冷漠,爱的忏悔
我喜欢它,Solid Base,神7慢摇
错过了缘分错过你,冷漠,冷漠的爱
我爱你亲爱的姑娘,布衣乐队,那么久
心锁,冷漠,心锁
爱される花爱されぬ花 (被爱的花,中島みゆき (中岛美雪),日韩经典三
口是心非,张雨生,张雨生精选集：永恒的经典
遇上你是我的缘,龚玥,民歌红1
幸福因为有你,星月组合,
下辈子做你的女人 (DJ版1),龙梅子,
青春修炼手册,TFBOYS,青春修炼手册
不仅仅是喜欢,孙语赛,不仅仅是喜欢
情网,高胜美,经典金选4 情难枕
明天你是否依然爱我,黑鸭子,男女情歌对唱
蓝莲花,许巍,时光·漫步
殇雪,云菲菲,
温柔与霸道,杭娇,温柔与霸道
两只老虎,杨烁,杨烁儿歌集
情人,杜德伟,
爱上你是我的错 + 擦肩而过,宇桐非,爱转了一圈
命运,Richard Clayderman,理查德克莱德曼黄金典藏三部曲
兰花草,杨烁,杨烁儿歌集
红尘有缘 (DJ版),DJ何鹏,DJ何鹏舞曲精选集（五）
歌声与微笑,新月合唱团,单曲-歌声与微笑
让泪化作相思雨,南合文斗,混了31年
恋人心,魏新雨,恋人心
真的好想你,卓依婷,蜕变2少女的心情故事
偏偏喜欢你,陈百强,偏偏喜欢你
信仰,张信哲,
在我心里从此有个你 (DJ版),DJ,DJ舞曲(华语)系列5
我爱爱爱爱爱着你,龙梅子,我爱爱爱爱爱着你
凉凉,杨宗纬,三生三世十里桃花 电视剧原声带
在他乡,水木年华,3
潇洒走一回 (Live),潘越云,梦想星搭档 第10期
下定决心忘记你,大哲,下定决心忘记你
一生无悔,高安,一生无悔
王妃,萧敬腾,王妃
为你打call,薛明媛,为你打call
水晶,任贤齐,任贤齐 & Friends
下定决心忘记你 (DJ阿远版),大哲,下定决心忘记你
女友嫁人新郎不是我,黑鸭子,印巴名歌
我是不是你最疼爱的人,高胜美,经典金选1
听着情歌流眼泪,龚玥,人声典范
十五的月亮,龚玥,军歌红
套马杆,龚玥,传奇之声
有多少爱可以重来,迪克牛仔,传奇
为爱痴狂,刘若英,少女小渔刘若英的美丽与哀愁
瓦尼莎的微笑,Richard Clayderman,理查德克莱德曼黄金典藏三部曲
飞呀飞 (DJ版1),龙梅子,
魔鬼中的天使,田馥甄,
不要在我寂寞的时候说爱我,T.R.Y,勇敢的女孩
泪满天 (DJ阿远 Remix),龙梅子,情歌继续唱
越南嗨鼓 (DJ版),7妹,电音王朝
倒带 (Live),王心凌,蒙面唱将猜猜猜第二季 第11期
奋进,,
我不配做你男朋友 (DJ Jack Remi,DJ,
不如跳舞,陈慧琳,花花宇宙
長い間 (长久),Kiroro,朝日快讯 VOL 09
四年半,杨清柠,四年半
喝着烈酒唱情歌,张冬玲,说好的一辈子(2011)
我要做你女朋友,Sunshine,我要做你女朋友
我爱的人不要走 (DJ阿远 Remix),龙梅子,情歌继续唱
做你心上的人 (DJ阿远 Mix),唐古,唐古风暴DJ热碟
我的心太乱,周传雄,我的心太乱
泪满天,龙梅子,情歌继续唱
为爱痴狂 (Live),刘若英,脱掉高跟鞋世界巡回演唱会
好心分手,王力宏,力宏二十 20周年唯一精选
倒带,蔡依林,城堡
不浪漫罪名,王杰,万岁2001
怒放的生命,汪峰,怒放的生命
不要在脸上留下眼泪,罗百吉,舞动人生
等你等了那么久 (独唱DJ版),祁隆,祁式情歌DJ精选
祈祷,黑鸭子,男女情歌对唱
奔跑 + 冷酷到底 (Live),羽泉,我是歌手第一季 总决赛
当你孤单你会想起谁,张栋梁,首选
盗心贼,黑龙,盗心贼
飘雪,陈慧娴,千千阙歌
给你们,张宇,雨一直下
走天涯,龚玥,我要去西藏
因为爱着你 (DJ 阿远 Club Exten,龙梅子,因为爱着你
前世今生的缘,云丹久美,前世今生的缘
苹果铃声 (越鼓版),7妹,电音霸主
谁的眼泪在飞,孟庭苇,谁的眼泪在飞
星月神话,金莎,
你的柔情我永远不懂,林雪,昨天的故事
山不转水转,龚玥,70恋歌
梦的翅膀受了伤,蒋雪儿,梦的翅膀受了伤
拯救,孙楠,缘分的天空
秋日的私语,Richard Clayderman,理查德.克莱德曼钢琴曲精选
我们的歌谣,T.R.Y,火花
别让我一个人醉,姜育恒,别让我一个人醉
我只在乎你,DJ小可,DJ小可 ⑥独孤求嗨
愿得一人心,李行亮,愿得一人心
你把爱情给了谁,龙梅子,赤裸裸的离开
卡农,Various Artists,结婚进行曲
我是不是你最疼爱的人,潘越云,我是不是你最疼爱的人
吻得太逼真,张敬轩,Urban Emotions
梦醒时分,高胜美,经典金选1
火红的萨日朗,乌兰托娅,火红的萨日朗
银,新疆美丽公主组合,欢乐地跳吧
让全世界知道我爱你 (DJ版),沈念,全部都给你
让全世界知道我爱你,六哲,让全世界知道我爱你
突然想起你,萧亚轩,萧亚轩 同名专辑
趁早,张宇,
手心手背,T.R.Y,爱有灵犀
大悲咒,龚玥,天女之声
一生所爱,卢冠廷,齐天周大圣之西游双记 电影歌乐?
梦驼铃,龚玥,金装小月
蓝色的爱,Richard Clayderman,理查德.克莱德曼钢琴曲精选
红尘情歌 (DJ Mosen Mix),高安,2016华语流行集锦二
以后的以后,庄心妍,庄心妍情歌精选集
凭着爱 + 再回首 (Live),卢冠廷,卢冠廷 2050 演唱会
逆流成河,白银河,有种音乐叫做白银河
我愿意 (管弦乐版),王菲,迷
十一年,邱永传,十一年
情路弯弯 (DJ阿远 Remix),龙梅子,情歌继续唱
爱河 (DJ版),神马乐团,浮云EP
爱河,蒋雪儿,爱河
单身情歌,林志炫,单身情歌 超炫精选
听心,杭娇,听心
秋的喁语 (Live),Richard Clayderman,理查德·克莱德曼钢琴曲全集-精?
做你心上的人,唐古,做你心上的人
床边故事,周杰伦,周杰伦的床边故事
女友嫁人 新郎不是我,DJ小可,古都情调“印度情歌”(Indian Lo
现代爱情故事,张智霖,EMI星声传集之张智霖
感动天感动地,宇桐非,与你同飞
这个年纪,齐一,这个年纪
水边的阿狄丽娜,Richard Clayderman,理查德.克莱德曼钢琴曲精选
你的爱情像闪电,龙梅子,你的爱情像闪电
爱的纪念,Richard Clayderman,理查德.克莱德曼钢琴曲精选
追梦人,高胜美,流金十载
回家 (萨克斯),Kenny G,金耳朵Ⅲ
走西口,龚玥,西部情歌
风中有朵雨做的云,孟庭苇,风中有朵雨做的云
好女人还有很多2017,杨海彪,好女人还有很多2017
我用自己的方式爱你,陈明真,我用自己的方式爱你
情非得已,庾澄庆,海啸
光,刘若英,一整夜
你是上天给我的礼物,星月组合,你是上天给我的礼物
煞科,郑秀文,Ladies First
小薇,龚玥,试音绝赏 发烧靓声
最爱的人伤我最深,张雨生,张雨生精选集：永恒的经典
因为爱着你,龙梅子,情歌继续唱
风中的承诺,李翊君,这样的我
最美的情缘,魏新雨,最美的情缘
不要在我的伤口撒盐,庄心妍,我知道
没有情人的情人节,孟庭苇,冬季到台北来看雨
大街小巷都听我的歌,马健涛,大街小巷都听我的歌
后来,刘若英,我等你
秋天不回来,王强,秋天不回来
秋日私语,Richard Clayderman,理查德克莱德曼黄金典藏三部曲
有点甜,汪苏泷,万有引力
小小新娘花,云菲菲,风的寂寞云知道
爱情买卖,慕容晓晓,爱情买卖
走西口,龚玥,民歌红 3
你的样子,林志炫,一个人的样子
以后的以后,庄心妍,一万个舍不得
突然的自我,伍佰,忘情1015精选辑
不要用我的爱来伤害我,韩晶,全年伤感歌曲大盘点3
你是我的玫瑰花(粤语版)

Atitit MP3元数据抽取记录 音乐信息检索

