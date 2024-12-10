Atitit pwa app prblm sulo


安卓的chrome没有弹添加到桌面的弹窗
检查你的manifest.json, sw.js文件是否在项目根目录下。以及sw是否注册成功。
如何判断是否从主屏幕访问
因为埋点等需求，我们需要区分用户是从浏览器访问的还是从主屏幕访问的，可以这样判断：
export const isFromDesktop = () => {
  // window.navigator.standalone used for safari
  if (window.navigator.standalone) {
    return true;
  }
  if (window.matchMedia && window.matchMedia('(display-mode: standalone)').matches) {
    return true;
  }
  return false;
};


如何监听添加到桌面事件
let deferredPrompt
window.addEventListener('beforeinstallprompt', event => {
  console.log('install event trigger', event);
  // 禁止浏览器自动显示添加到桌面提示框
  e.preventDefault();
  // 存储事件对象，方便后面自定义弹窗时机
  deferredPrompt = e;

  // 然后可以显示一个自定义的提示框给用户，告诉用户
  // 可以将应用添加到桌面，同时可以告知如何操作
})

// 再监听自定义提示框的按钮点击事件
buttonInstall.addEventListener('click', (e) => {
  // 隐藏我们自定义的弹窗
  hideMyInstallPromotion();
  // 显示添加到桌面提示框（浏览器提供的）
  deferredPrompt.prompt();
  // 这里可以获取到用户的选择，同时做一些埋点相关操作
  deferredPrompt.userChoice.then((choiceResult) => {
    if (choiceResult.outcome === 'accepted') {
      console.log('用户接受');
    } else {
      console.log('用户拒绝');
    }
  })
});

添加到主屏幕失败
安卓浏览器添加到主屏幕权限可能没打开，如果没打开，也不会有添加到主屏幕那个提示框的，需要开启权限再次尝试（所以一个自定义的提示框还是很重要的，可以告知用户如何处理失败的情况，经过测试，因为权限导致的失败并没有什么提示给到用户）
如何捕捉安装成功动作
window.addEventListener('appinstalled', (evt) => {
  console.log('app installed', evt);
})


全局本页面打开  a标签  self
<base target="_self" />


<script defer>
    function portionA(){
        //getElementById("portionA").
        var aN = document.getElementsByTagName("a");
        for(var i =0; i < aN.length; i++){
            aN[i].target ="_self";/*遍历局部a标签并设置target属性值*/
        }
    }
    portionA();//调用函数
    window.setInterval(portionA,100);

</script>


Ref
Atiti pwa app的初步安装体系
Atitit atit it pwa Service Worke重要api
Atitit pwa prblm重大问题与解决总结v2
Atitit pwa 技术总结 v2
Atitit pwa调试渐进式 Web 应用程 v2
Atitt pwa net first cache 策略core code
