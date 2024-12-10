Atitit 序列化知识点


二进制vs文本模式序列化
语言相关的序列化 php java js序列化（json

语言无关的序列化 xml   url参数
数据交换与序列化
Ini xml yml json csv

几种常见的序列化和反序列化协议
互联网早期的序列化协议主要有COM和CORBA。
Json序列化
、

ref
Atitit data fmt sumup 常用的数据交换格式    标准


目录
1. 分类标准	2
1.1. 按照结构化与非结构化分类	2
1.2. 按照资料性质分类常见的数据格式txt ，doc ，pic，music ，vodio	2
1.3. 通用与专用格式	2
1.4. 完全与受限 比如xml和ini	2
1.5. 文本 vs 二进制	2
1.6. 工业标准vs私有标准 json vs  java php str	2
2. 通用格式json yaml toml xml Html	2
2.1. Serialize phpstr  javastr	2
2.2. 源码 and ast	2
2.3. 变量     将数据写成标准的PHP赋值语句存放在文本文件中，在程序执行过程中包含进来，	2
2.4. 非完全格式Urlparam Prop、ini csv csvWzHead3	3
2.5. TLV（三元组编码）：  T（标记/类型域）L（长度/大小域）V（值/内容域），	3
3. 专用格式	4
4. 专用格式.常用格式	4
4.1. Diary 格式	4
4.2. 财务记录excel	4
4.3. 用户信息vcf 通讯录导出的一种格式	4
4.4. 导入导出数据csv,excel格式	4
4.5. Browser ,fav data ,html format..eg 360se	4
4.6. Zip  rar	4
4.7. Music Lrc歌词  mid	4
5. 专用格式 . 其他	4
5.1.1. 邮件格式eml	4
5.1.2. Im	4
5.1.3. Doc ，docx	4
5.1.4. 翻译软件词条,haosyo 马个标准的..使用txt xml的有..	4
5.1.5. 视频元数据 info	4
5.1.6. 输入法，词库格式	5
5.1.7. News  ，rss vs atom	5
5.1.8. Dev ,sql	5
5.1.9. 商品信息excel  ecshop标准	5
5.1.10. 地图，地理位置格式	5
5.1.11. 日历格式，excel格式，貌似没有标准格式	5
5.1.12. 天气软件格式	5
6. Ref	5
6.1. Atitit.常见软件 数据 交换格式 标准.docx	5

