Atitit.excel类库  选型 java  总结

目前应用比较多的处理Excel的类库主要有两种JXL 和POI。
都是开源项目，POI是apache下的子项目，经过研究和比较觉得POI更新更快一些。
到目前为止已经支持Excel2007版本了，不过目前也是3.5的beta4版以上才支持。JXL貌似还不行，但是个人觉得在使用上JXL简单一些。
另外JXL还有一个小问题需要注意一下在读取Excel文件是单次读不可以超过10000行，否则会溢出。经过试验9999可以，10000就不行了，不知道jxl为什么要控制在这个数。
因此如果兄弟们需要单次读取大数据量的时候需要手工处理下，分次读取就可以了。
因此建议处理EXCEL97-2003时可选用JXL，处理2007版本可选择POI，
