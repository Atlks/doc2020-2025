Atitit 字符编码与转义  java


 特殊字符：就3个  单双引号与反斜杠
      \"： 双引号
     \'： 单引号
     \\：反斜线


Xxx进制与unicode转义字符
进制转义序列：\ + 1到3位5数字；范围'\000'~'\377'
      \0：空字符
2.Unicode转义字符：\u + 四个 十六进制数字；0~65535
     \u0000：空字符


4. 控制字符：5个  回车换行跳格退格等


\' 单引号字符

\\ 反斜杠字符

\r 回车

\n 换行

\f 走纸换页

\t 横向跳格

\b 退格

	private static String encodeJavaMsg(String msg) {

		char c = '\\';
		String replacement = String.valueOf(c) + "" + String.valueOf(c);
		msg = msg.replaceAll("\\\\", "\\\\\\\\");

		msg = msg.replaceAll("\n", "\\\\n");
		msg = msg.replaceAll("\r", "\\\\r");
		msg = msg.replaceAll("\"", " \\\" ");
		return msg;
	}
}1、转义字符反斜杠（\）
　　我们知道html中大都是双标签，如果在标签内想要输出带有标签结束符的文本都必须进行转义，html中是采用对应的字符替换，如<可用&lt;替换
　　在java当中，我们要转义一个字符使用的是反斜杠\,反斜杠的作用就是转义下一个字符
2、回车符\r
　　\r在java中是回车符的意思，将光标切换到当前行的开头
3、换行符\n
　　\n在java中是换行符的意思，切换到下一行，且将光标切换到下一行的开头
4、制表符\t
　　\t是制表符的意思，将光标移动到下一个制表符的位置，相当于键盘中的windows键
5、退格符\b
　　\b是退格符的意思，将光标回退一个字符的位置，可以结合空白字符使用达到类似删除的效果
前面5个都是具有特殊含义，下面的是将特殊含义取消的转义
6、\"双引号字符
　　如果需要在双引号内输出双引号字符，且不需要让他产生双引号开始结束的效果，则需要使用这种被转义过的引号
7、\'单引号字符
　　如果需要在单引号内输出单引号，且要求不对我们的引号产生什么不良效果，则需要使用这种被转义过的引号
8、\\ 反斜杠字符
　　如果想要输出单纯的反斜杠，就必须在原来的基础上再进行转义一次，让反斜杠失去转义字符的效果
例子：
/*
反斜杠\是一个特殊的字符，在java中在java中被称为转义字符，作用是转义后面一个字符
\r表示回车，将光标定位到当前行的开头，不会跳到下一行
\n表示换行，换到下一行的开头
\t表示制表符，将光标移动到下一个制表符的位置，相当于Tab键
\b表示退格符，就像键盘上的Backspace键*/public class SpecialCharacter {
        public static void main(String[] args) {
            System.out.println("\\");
            System.out.println("a\rb");
            System.out.println("a\nb");
            System.out.println("a\tb");
            System.out.println("a\bb");
            System.out.println('\'');
            System.out.println("\"");
        }
}

