Go doc


godoc 命令
　　我们从工具命令开始讲起吧。在 2019 年之前，Go 使用的是 godoc 这个工具来格式化和展示 Go 代码中自带的文档。现在这个命令已经不再包含于 Go 工具链中，而需要额外安装: 
go get -v golang.org/x/tools/cmd/godoc
　　godc 命令有多种模式和参数，这里我们列出最常用和最简便的模式：
cd XXXX; godoc -http=:6060
godoc -http=:6060

godoc godoc命令主要用于在无法联网的环境下，以web形式，查看Go语言标准库和项目依赖库的文档。
