Atitit android webview  useage


百分百展示 "match_parent
<WebView  
android:layout_width="match_parent"  
android:layout_height="match_parent"  
android:id="@+id/webView"  
/>  

/覆盖WebView默认使用第三方或系统默认浏览器打开网页的行为，使网页用WebView打开
//覆盖WebView默认使用第三方或系统默认浏览器打开网页的行为，使网页用WebView打开  
webView.setWebViewClient(new WebViewClient(){  
@Override  
public boolean shouldOverrideUrlLoading(WebView view, String url) {  
// TODO Auto-generated method stub  
//返回值是true的时候控制去WebView打开，为false调用系统浏览器或第三方浏览器  
view.loadUrl(url);  
return true;  
}  
});  



onReceivedSslError()
SSL 证书验证错误
比如处理 https 请求时，webView 默认时不处理 https 请求的，页面显示空白。
webView.setWebViewClient(new WebViewClient() {    
        @Override    
        public void onReceivedSslError(WebView view, SslErrorHandler handler, SslError error) {    
            handler.proceed();    //表示等待证书响应
        // handler.cancel();      //表示挂起连接，为默认方式
        // handler.handleMessage(null);    //可做其他处理
        }    
    });


3.2 WebChromeClient
和 webView 的网页内容管理有关，它的成员方法帮助 WebView 处理 JS 的弹框、网站图标、网站title，加载进度等等。
  // 设置 WebChromeClient
 mWebView.setWebChromeClient(mWebChromeClient);
4. 网页的前进与后退
在 Android 中 如果在 WebView 触发物理返回键会直接关闭整个 WebView，所以需要监听事件，用 WebView 的返回处理。
webView.goBack();//跳到上个页面
webView.goForward();//跳到下个页面
webView.canGoBack();//是否可以跳到上一页(如果返回false,说明已经是第一页)
webView.canGoForward();//是否可以跳到下一页(如果返回false,说明已经是最后一页)
实际项目中可以可以监听物理键的返回键，也可以重写 onBackPressed()方法，以下代码段仅做参考：
@Overridepublic boolean onKeyUp(int keyCode, KeyEvent event) {
    if (KeyEvent.KEYCODE_BACK == keyCode) {
        if (mWebView != null && mWebView.canGoBack()) {
            mWebView.goBack();
        } else {
            finish();
        }
        return true;
    }
    return super.onKeyUp(keyCode, event);}
5. 缓存
加载 html 界面时：
当加载 html 页面时，WebView 会在/data/data/包名目录下生成 database 与 cache 两个文件夹。
请求的 URL记录保存在 WebViewCache.db，而 URL的内容是保存在 WebViewCache 文件夹下。
缓存方式
settings.setCacheMode(WebSettings.LOAD_NO_CACHE);
LOAD_CACHE_ONLY: 不使用网络，只读取本地缓存数据
LOAD_DEFAULT: （默认）根据cache-control决定是否从网络上取数据
LOAD_NO_CACHE: 不使用缓存，只从网络获取数据
LOAD_CACHE_ELSE_NETWORK：只要本地有，无论是否过期，或者no-cache，都使用缓存中的数据
PS：这里还有其他和缓存相关的，由于还没有搞的很清楚，暂时不总结了


作者：tingtingtina
清除缓存
//清除网页访问留下的缓存//由于内核缓存是全局的因此这个方法不仅仅针对webview而是针对整个应用程序.
webView.clearCache(true);
//清除当前webview访问的历史记录//只会webview访问历史记录里的所有记录除了当前访问记录
webView.clearHistory();
//这个api仅仅清除自动完成填充的表单数据，并不会清除WebView存储到本地的数据
webView.clearFormData();


访问内部html
C:\Users\ati\AndroidStudioProjects\hxc3\app\src\main\assets\t.htm
webView.loadUrl("file:///android_asset/t.htm");//加载asset文件夹下html

Ref


WebView 使用和方法（持更） - 简书

Atitit android app 最佳实践2021

目录
1. Android strudio,,and viruse machine need down another...	1
1.1. Prj,, empty active  no active  vs	1
1.2. MainActivity。Kt,,指明启动那个view	2
1.3. Res/layout/activemain.xml     是view	2
2. 1 Android 中的资源文件	2
3. 4 res/raw 和 assets 使用场景	3
3.1. 百分百宽度高度问题	3
3.2. 打包apk	3
4. Prblm	3
4.1. Function invocation 'WebView(...)' expected	3
4.2. 驱除默认标题栏	4
5. Code	5

