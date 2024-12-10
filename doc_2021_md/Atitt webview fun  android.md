Atitt webview fun  android
hxc3

C:\Users\ati\AndroidStudioProjects\hxc3\app\src\main\java\com\example\hxc3\MainActivity.kt

package com.example.hxc3

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.webkit.WebSettings
import android.webkit.WebView
import android.webkit.WebViewClient


class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)


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


        webView.loadUrl("file:///android_asset/hxc_idx.html");//加载asset文件夹下html


    }
}
