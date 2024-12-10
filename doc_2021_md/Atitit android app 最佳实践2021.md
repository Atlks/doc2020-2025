Atitit android app 最佳实践2021

Android strudio,,and viruse machine need down another...

Prj,, empty active  no active  vs 

androidmanifest..xml
Zhimin  启动类

<activity
    android:name=".MainActivity"




MainActivity。Kt,,指明启动那个view


package com.example.hxc3

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
Res/layout/activemain.xml     是view

1 Android 中的资源文件
Android 资源文件大致可以分为两种：res/raw 和 assets

res/raw
res/raw 目录下存放可编译的资源文件
这种资源文件系统会在 R.Java 里面自动生成该资源文件的 ID，所以访问这种资源文件比较简单，通过 R.XXX.ID 即可。
assets
assets目录下存放原生资源文件，可以存放一些图片，html，js, css等文件。
————————————————
4 res/raw 和 assets 使用场景
由于 res/raw 是Resources(res)的子目录，Android会自动的为这目录中的所有资源文件生成一个ID，这个ID会被存储在R类当中，作为一个文件的引用。这意味着这个资源文件可以很容易的被Android的类和方法访问到，甚至在Android XML文件中你也可以@raw/的形式引用到它。在Android中，使用ID是访问一个文件最快捷的方式。MP3和Ogg文件放在这个目录下是比较合适的。
assets 目录更像一个附录类型的目录，Android不会为这个目录中的文件生成ID并保存在R类当中，因此它与Android中的一些类和方法兼容度更低。同时，由于你需要一个字符串路径来获取这个目录下的文件描述符，访问的速度会更慢。但是把一些文件放在这个目录下会使一些操作更加方便，比方说拷贝一个数据库文件到系统内存中。要注意的是，你无法在Android XML文件中引用到assets目录下的文件，只能通过AssetManager来访问这些文件。数据库文件和游戏数据等放在这个目录下是比较合适的。
————————————————
  (229条消息) Android -- 读取assets文件夹下的资源_一只驴在敲代码-CSDN博客_读取assets文件
百分百宽度高度问题
match_parent


打包apk
必须要menu》build》apk才可，，否则默认debug的虚拟机只适合虚拟机的版本，真实机器无法安装


更换logo
New img asset》》load pic choose 。。。即可。。会自动替换五六个文件夹下面的logo资源
Prblm

Function invocation 'WebView(...)' expected

使用kontolin语法，不要在kt文件里面使用java语法

    var webView = findViewById(R.id.webView1) as WebView;

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

          // webView = (WebView)findViewById(R.id.webView1);
        var webView = findViewById(R.id.webView1) as WebView;
               //new WebView(new MutableContextWrapper(this));
        // 设置WebView属性，能够执行Javascript脚本
        webView.getSettings().setJavaScriptEnabled(true);
    //    webview.settings.javaScriptEnabled = true
        webView.loadUrl("https://www.bbc.com/zhongwen/simp");
    }
}
驱除默认标题栏
进入第一个Activity界面，就会发现，该界面顶部已经出现了默认的背景为蓝色的标题栏，标题栏的文字就是应用程序的名字，这是系统默认的，如果开发者没有设置Activity的label标签，那么就会默认使用程序名。

supportActionBar?.hide();


Code

  //hide title bar
     supportActionBar?.hide();


       // webView = (WebView)findViewById(R.id.webView1);
     var webView = findViewById(R.id.webView1) as WebView;
            //new WebView(new MutableContextWrapper(this));


     // 设置WebView属性，能够执行Javascript脚本
     webView.getSettings().setJavaScriptEnabled(true);
 //    webview.settings.javaScriptEnabled = true



     //开启https he http红和内容
     var webSettings= webView.getSettings();
     webSettings.setMixedContentMode(WebSettings.MIXED_CONTENT_ALWAYS_ALLOW);
  //   webView.loadUrl("https://hxcsxs.xsitehub.com/");



     //1.2.覆盖WebView默认使用第三方或系统默认浏览器打开网页的行为，使网页用WebView打开
   //  webView.setWebViewClient(new WebViewClient());
     //kotlin
     webView.webViewClient = WebViewClient()


//     webView.loadUrl("file:///android_asset/hxc_idx.html");//加载asset文件夹下html
   webView.loadUrl("https://h /index_app/index_app.html");//加载asset文件夹下html

