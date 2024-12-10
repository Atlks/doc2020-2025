Atitit 蓝牙开发 搜索蓝牙设备 java noede.js python

先查询跨语言类库wmi 结果貌似没有 
没有shell工具
java资料bluecove
Node.js但是需要替换驱动麻烦。。
搜索Python库看看 
需要安装替换vc sdk ，pass
Powershell 试试看  貌似没有提示不好做

安装vscode  net包管理器插件paket，然后下载蓝牙库32feet.NET

C:\Users\aaa.ATTILAXPC188\.vscode\extensions\ionide.ionide-paket-1.12.0\bin\paket.exe add nuget 32feet.NET



using System;
using System.Collections.Generic;
using InTheHand.Net;
using InTheHand.Net.Bluetooth;
using InTheHand.Net.Sockets;
using Newtonsoft.Json;
using System.Configuration;
using System.IO;
using System.Reflection;

namespace eee
{
    class Program
    {
        static void Main(string[] args)
        {

                 //  #pragma comment(lib, "dll\System.Configuration.dll");
                  var path = new FileInfo(Assembly.GetExecutingAssembly().Location);
                 var a = Assembly.LoadFile(Path.Combine(path.DirectoryName, "lib\\System.Configuration.dll"));
                //InTheHand.Net.Sockets.BluetoothClient
                 Console.WriteLine(System.Configuration.Assemblies.AssemblyHashAlgorithm.MD5);
               
                BluetoothClient Blueclient = new BluetoothClient();
                Dictionary<string, BluetoothAddress> deviceAddresses = new Dictionary<string, BluetoothAddress>();

           //     Newtonsoft.JsonConvert
                BluetoothRadio BuleRadio = BluetoothRadio.PrimaryRadio;
                BuleRadio.Mode = RadioMode.Connectable;
                BluetoothDeviceInfo[] Devices = Blueclient.DiscoverDevices();
                //  System.Configuration.dll
                Console.WriteLine(    Newtonsoft.Json.JsonConvert.SerializeObject(Devices) );
                Console.WriteLine("Hello World!");
        }
    }
}


 

用C#调用蓝牙编程 - ZWmaqing - 博客园.mhtml
如何在C＃中仅发现打印机蓝牙设备？ - 问答 - 云+社区 - 腾讯云.mhtml
