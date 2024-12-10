Atitit netcore 问题与解决


Prblm

 dotnet new console -o Walterlv.Demo
dotnet : 无法将“dotnet”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保路径正确，然后再试一次。
所在位置 行:1 字符: 1
+ dotnet new console -o Walterlv.Demo
    + CategoryInfo          : ObjectNotFound: (dotnet:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
分析原因#

ASP.NET Core 2.1以上的版本中，Microsoft.EntityFrameworkCore.Tools 包包含在 Microsoft.AspNetCore.App元包。
而 ASP.NET Core 2.1 以下的版本中需要手动引用 Microsoft.EntityFrameworkCore.Tools包。
解决问题#

只需要在程序包管理器控制台，输入如下图命令即可：
PM> Install-Package Microsoft.EntityFrameworkCore.Tools

导入第三方dll库
Nuget太麻烦，
使用dll本地导入

*。Csproj  只是添加应用dll，实际放在lib下面就可以自动可以了
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Reference Include="log4net">
      <HintPath>dll\log4net.dll</HintPath>
    </Reference>

     <Reference Include="InTheHand.Net.Personal">
      <HintPath>dll\InTheHand.Net.Personal.dll</HintPath>
    </Reference>


      <Reference Include="Newtonsoft.Json">
      <HintPath>dll\Newtonsoft.Json.dll.dll</HintPath>
    </Reference>

  </ItemGroup>

</Project>


跨平台开发netcore程序

本篇文章编写环境为windows 10 ，dotnet 命令同样适用于其它系统。
配合 VS Code 你就可以在 Linux 、MAC 上开发.NET Core


不能生产dll问题，可能是360杀毒监控了。。
运行dll问题
otnet run 执行程序

 
dotnet xx.dll 也是执行程序
"C:\Program Files\dotnet\dotnet.exe" C:\0workspace\bluetoothPrj\bin\Debug\netcoreapp2.2\Walterlv.Demo.dll
交叉编译 publish


_NET Core dotnet 命令大全 - LineZero - 博客园.mhtml

