Atitit golan dev envi useage



Install   100M  Ide  vscode

go version go1.15.6 windows/amd64

新建
Go的二进制编译包假设你把Go安装在 /usr/local/go (或者Window是 c:\Go)目录下。当然你也可以安装在其他目录下，不过这时候你就需要设置GOROOT环境变量了。
http://golang.org/doc/install#install
例如，你如果安装Go在你的Home目录下，你应该$HOME/.profile文件增加下面设置。
 
export GOROOT=$HOME/go
export PATH=$PATH:$GOROOT/bin
Window下则是：

GOPATH
GOPATH的作用是告诉Go 命令和其他相关工具，在那里去找到安装在你系统上的Go包。
GOPATH是一个路径的列表，一个典型的GOPATH设置如下，类似PATH的设置，Win下用分号分割：
GOPATH=/home/user/ext:/home/user/mygo
Launch.json 可以add config

    "configurations": [
        {
            "name": "Launch file",
            "type": "go",
            "request": "launch",
            "mode": "debug",
            "program": "${file}",
          
          
            "showLog": true
        },
"env"为设置环境变量, 设置为你的工程目录就可以(包含bin, src的文件夹) 默认｛｝，可以不设置

Down sub lib

go get -u github.com/go-sql-driver/mysql



使用 Ide选择liteide  更加方便，有代码提示
Vs对没有提示2020.ub  。。搞了洗没搞出来


执行 Go 程序的三种方式及 Go 语言关键字
执行 Go 程序的三种方式
一、使用 go run 命令


二、使用 go build 命令
Step1. 对 go 源码源文件执行 go build 命令，会生成一个同名 .exe的可执行文件
Step2. 执行.exe可执行文件


三、在线编译运行
使用官方网站的在线工具进行编译运行：https://play.golang.org

Halo

运行 ，会提示下载  dlv cmd工具。。
Installing github.com/go-delve/delve/cmd/dlv (C:\Users\ati\go\bin\dlv.exe) SUCCEEDED

All tools successfully installed. You are ready to Go :).


Rest 接口服务提供


调研rest接口 http接口 ok

调用mysql

ref


Atitit golang开发环境搭建 目录 1. 编辑helo.go 1 1.1. 调试编译 1 2. Ide选择liteide 2 3. 问题解决 2 4. 附录 2 4.1. Go语言标准库常_attilax的专栏-CSDN博客
Atitit golang开发环境搭建 目录 1. 编辑helo.go 1 1.1. 调试编译 1 2. Ide选择liteide 2 3. 问题解决 2 4. 附录 2 4.1. Go语言标准库常_attilax的专栏-CSDN博客

