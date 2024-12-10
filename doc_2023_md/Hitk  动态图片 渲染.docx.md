Hitk  动态图片 渲染

的生成一些图片，图片的格式要求也比较严格就像是这样的


表格中的数据如 单价 数量都是动态的数据，刚开始准备用 GD库 来操作，后来想想不太现实所以去找了找有没有比较成熟的 php 类库。有不少的类库，可以实现直接生成 PDF 而没有可以直接生成 Image 的扩展包。

然后pdf转换为img

Php很麻烦，生成pdf容易使用MPDF。转换img麻烦。。
Nodejs 更加简单 。。Puppeteer 可以截屏






2.使用MPDF类生成PDF的方法
mPDF是一个PHP类，它可以从UTF-8编码的HTML生成PDF文件，它基于FPDF和HTML2FPDF，并具有许多增强功能。对于语言处理和UTF-8支持，mpdf优于FPDF。对于CJK支持，它不仅支持字体嵌入，而且支持字体子集（所以您的CJK PDF不会过大）。


新项目有一个将数据导出PDF文件格式的需求，研究一段时间后发现利用PHP编码生成PDF文件是一个非常耗时的工作，还好已经有很多函数库可以使用了，并且能够从你提供的HTML文件生成PDF文档，mPDF就是一个不错的选择,mPDF能基本兼容HTML标签和CSS3样式。


TCPDF
————————————————
原文:使用PHP生成PDF文档 
实际工作中，我们要使用PHP动态的创建PDF文档，目前有许多开源的PHP创建PDF的类库，今天我给大家来介绍一款优秀的PDF库，它就是TCPDF，TCPDF是一个用于快速生成PDF文件的PHP5函数包。TCPDF基于FPDF进行扩展和改进，增强了实用功能。


后来发现了一个 开源的软件 wkhtmltox 该软件支持读取本地和网络端的网页，直接在本地生成 pdf 或 image。wkhtmltox 官方地址

