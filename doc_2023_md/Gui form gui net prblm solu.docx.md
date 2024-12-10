Gui form gui net prblm solu


Cant finds window.external


Maybe only winform app..u should use windows form app(net frwk）







    // 这样使得C#的com对象是对网页里的javascript可见的。
    [System.Runtime.InteropServices.ComVisible(true)]
    public partial class Form1 : Form
    {
       

        private void Form1_Load(object sender, EventArgs e)
        {
            WebBrowser browser = new WebBrowser();

            //   ChromiumWebBrowser WebBrowser = new ChromiumWebBrowser();
            //注册script 调用对象   通过window.external捕获调用c#定义好的函数。
            browser.ObjectForScripting = this;  // 将当前类设置为可由脚本访问
                                                //    browser.Regis

            browser.Dock = DockStyle.Fill;
            this.Controls.Add(browser);
            //   MessageBox.Show(System.Environment.CurrentDirectory);

            //  browser.Navigate(System.Environment.CurrentDirectory+"/index.html");
            //   browser.Navigate("C:\\modyfing\\apiprj\\jbbot\\zmng\\js2net.html");
            browser.Navigate("C:\\modyfing\\apiprj\\jbbot\\zmng\\index.html");
            // objects[0] = “C#访问JavaScript脚本";
            //	this.webBrowser1.Document.InvokeScript("messageBox", objects);
        }



        public void invkFrmWeb(string cmd)
        {
            MessageBox.Show(cmd);
        }




        public void errorHandler(string errJson)
        {
            MessageBox.Show(errJson);
        }
Xx.js

window.external.invkFrmWeb("自定义弹窗");


window.onerror = function(message, url, lineNumber)
{


   let eobj={"msg":message,"url":url,"line":lineNumber};

   window.external.errorHandler( JSON.stringify(eobj) );
}



.NET 版本更新了一代又一代，winform中的webbrowser控件的IE内核版本却始终用的IE7，好多网站都对IE7已经不支持。webbrowser这个控件就显得有些鸡肋，经过查找大佬门的代码和资料，终于找到了


  case 10:
                    mode = 10000; // Internet Explorer 10.  
                    break;
                case 11:
                    mode = 11000; // Internet Explorer 11.


切换模式后好很多了，但是默认webbrower一然不支持js一些高级用法，，nullsafe语法等。。
切换框架到cef把事实看

CEF 全称是Chromium Embedded Framework（Chromium嵌入式框架），是个基于Google Chromium项目的开源Web browser控件，支持Windows, Linux, Mac平台。CEFSharp就是CEF的C#移植版本。
就是一款.Net编写的浏览器包，方便你在Winform和WPF中内嵌的Chrome浏览器组件
Cef兼容性很好，但是体积太大了，300M，打包后都有100M

