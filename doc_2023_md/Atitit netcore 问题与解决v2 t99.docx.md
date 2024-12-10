Atitit netcore 问题与解决


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

