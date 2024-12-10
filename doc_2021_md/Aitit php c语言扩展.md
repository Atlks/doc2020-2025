Aitit php c语言扩展  

最后，我们尝试创建一个 .c 文件，比如 hello.c，内容如下：
#include <stdio.h>
int main(){
    printf("Hello, world!");}


Vscode会提示加载下载c cpp语言扩展

C/C++ for Visual Studio Code

编译运行



是的，这相当于在当前目录下执行了 gcc hello.c -o hello 后再自动执行了生成的 hello.exe 文件。
整个过程就是这样，另外 Mingw-w64 是用 gcc 进行编译的，如果要用 clang 就得安装 LLVW，这里不做赘述，事实上初学 C 这样就够了。


 
先下载安装如下应用：
Mingw-w64 是一个工具集，提供在 Windows 下的 C 语言开发环境，包含了头文件、库、运行时和一些工具，支持64位开发，是 MinGW 的升级项目。官方提供的 installer 托管在 sourceforge 上，安装过程是需要联网的，对于国内的网络环境来说极其困苦，所以还是建议下载对应版本的压缩包来自己配置：


其实没必要了，使用java扩展更快。。



在 Visual Studio Code 下配置 C 语言运行环境 - 简书

