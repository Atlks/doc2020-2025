Go 模块管理  找不到模块解决方法

解决方案

方案一：关闭go mod
这个方案非常简单，只需要在命令行输入以下命令即可

go env -w GO111MODULE=off

    1.

方案二：将项目转为module（模块）
进入项目目录demo_51_package下，输入以下2个命令

# 初始化模块-- init 后面的名称一定要和项目目录相同
go mod init demo_51_package

# 下载依赖包
go mod tidy

    1.
    2.
    3.
    4.
    5.

执行后会发现，项目下多了个go.mod的文件
【go】goland编写go语言导入自定义包出现： package xxx is not in GOROOT (/xxx/xxx) 的解决方案_main方法_03

这个文件内容也非常简单，只有2行数据

module demo_51_package

go 1.17

    1.
    2.
    3.

在次运行
配置完成后，在编译并执行main方法，发现已经可以正常运行了
-----------------------------------
【go】goland编写go语言导入自定义包出现： package xxx is not in GOROOT (/xxx/xxx) 的解决方案
https://blog.51cto.com/u_15694353/5410704


它有三个可选值：off、on、auto，默认值是auto。
GO111MODULE=off禁用模块支持，编译时会从GOPATH和vendor文件夹中查找包。
GO111MODULE=on启用模块支持，编译时会忽略GOPATH和vendor文件夹，只根据 go.mod下载依赖。
GO111MODULE=auto，当项目在$GOPATH/src外且项目根目录有go.mod文件时，自动开启模块支持。
在使用 go modules 模式后，项目目录下会多生成两个文件也就是 go.mod 和 go.sum 。
这两个文件是 go modules 的核心所在，这里不得不好好介绍一下。



五、go mod 命令的使用
go mod init：初始化go mod， 生成go.mod文件，后可接参数指定 module 名，上面已经演示过。
go mod download：手动触发下载依赖包到本地cache（默认为$GOPATH/pkg/mod目录）
go mod graph： 打印项目的模块依赖结构
go mod tidy ：添加缺少的包，且删除无用的包
go mod verify ：校验模块是否被篡改过
go mod why： 查看为什么需要依赖
go mod vendor ：导出项目所有依赖到vendor下
go mod edit ：编辑go.mod文件，接 -fmt 参数格式化 go.mod 文件，接 -require=golang.org/x/text 添加依赖，接 -droprequire=golang.org/x/text 删除依赖，详情可参考 go help mod edit
go list -m -json all：以 json 的方式打印依赖详情
如何给项目添加依赖（写进 go.mod）呢？
有两种方法：
你只要在项目中有 import，然后 go build 就会 go module 就会自动下载并添加。
自己手工使用 go get 下载安装后，会自动写入 go.mod 。

