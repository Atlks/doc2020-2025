Atitit 货币数字的格式化显示

展示俩位小数




private static Object roundUP(String format) {
    String price_pre=format.substring(0,format.length()-1);
    int lastNum=Integer.parseInt( format.substring(format.length()-1));
    if(lastNum>0 && lastNum<5)
        return price_pre+"5";
    if(lastNum>=5 && lastNum<=9)
    {
        Double d=   Double.parseDouble(price_pre)+0.10d;
        DecimalFormat df2 = new DecimalFormat("##0.00");//这样为保持2位
        return df2.format(d);
    }

    return    format ; // 0 5
}





使用DecimalFormat之后，如果小数点前面是0，则直接不显示的解决方法
2018-07-20 17:07:15 无小旭 阅读数 4719更多
分类专栏： 开发用笔记
版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。
本文链接：https://blog.csdn.net/qq_33339175/article/details/81135556
api中文帮助文档关于”#”的翻译是错误的，原文为“zero shows as absent”译为“如果为0，则不显示”。
代码示例：
new  java.text.DecimalFormat("#.###").format(3.0)new  java.text.DecimalFormat("0.000").format(3.0)
1
2
输出的结果为： 3 和3.000
“#”可以理解为在正常的数字显示中，如果前缀与后缀出现不必要的多余的0，则将其忽略。

