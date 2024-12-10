Atitit pwa自定义安装到桌面提示

几个注意事项
deferredPrompt.prompt();  // Wait for the user to respond to the prompt
必须按钮触发。。不能在js代码里面自动触发。。直接触发

<!-- pwa add2dsktp tips -->
<script src="/js\layer-v3.5.1\layer\layer.js"></script>
<div id="tips88" style="padding: 10px;display: none">
    <table width="100%">
        <tr><td width="70">  <img  style="border-radius: 9px;" src="/images/logo.png" width="60" height="60"></td><td style="padding: 7px;">将含羞草添加到手机桌面<br> 随时随地想看就看<br> hxc.one</td></tr>
        <tr style="font-size: 20px; font-weight: bolder"><td></td><td align="right">
            <div align="right">
                <button style="color: #8605c2;margin-right: 40px;" onclick="truePwaInstallFun()">同意</button>
                <button style="color: grey" onclick="closeLayer()">我再想想</button>
            </div>
            </td></tr>
    </table>
</div>
<script id="pwajs" src="/pwa/add2dsktp.js" defer></script>
<!-- pwa add2dsktp tips  end -->










function  closeLayer(){
    layer.close(index88)
}
var deferredPrompt;
var index88;
function myTps() {
    $("#tips88").show();
    index88 =  layer.open({
        type: 1,title:'',  time: 12000,
        area: ['370px', '140px'],
        end: function () {
            //无论是确认还是取消，只要层被销毁了，end都会执行，不携带任何参数。layer.open关闭事件
            $("#tips88").hide();
        },
        content: $('#tips88') //这里content是一个DOM，注意：最好该元素要存放在body最外层，否则可能被其它的相对元素所影响
    });
    window.setTimeout(()=>{
        $("#tips88").hide(); layer.close(index88);
    },12000);


}

function  truePwaInstallFun()
{
    //  layer.close();

    console.log(' truePwaInstallFun()')
    //alert("即将添加pwa应用。")
    //use client aft evenet
    // 隐藏我们自定义的弹窗
    //  hideMyInstallPromotion();
    // 显示添加到桌面提示框（浏览器提供的）
    //   deferredPrompt.prompt();
    // 这个 `event.userChoice` 是一个 Promise ，在用户选择后 resolve
    deferredPrompt.prompt();  // Wait for the user to respond to the prompt


    /**
     * type UserChoice = {
  outcome: "accepted" | "dismissed";
  platform: string;
};
     */
    //// 这里可以获取到用户的选择，同时做一些埋点相关操作
    deferredPrompt.userChoice.then(result => {
        console.log(result.outcome)
        closeLayer();
        // 'accepted': 添加到主屏
        // 'dismissed': 用户不想理你并向你扔了个取消
    },handleError88);
}
function  handleError88(e)
{
    console.log(e)
}
// 「弹出添加到主屏对话框」事件
//   const.o();   jeig script err ,cant effe next js
console.log('before install window.addEventListener')
window.addEventListener('beforeinstallprompt', event => {
    console.log('before install prompt')
    // 禁止浏览器自动显示添加到桌面提示框
    //    event.preventDefault();
    console.log(event.platforms); // e.g., ["web", "android", "windows"]

    // 存储事件对象，方便后面自定义弹窗时机
    deferredPrompt = event;
    myTps();
    // 然后可以显示一个自定义的提示框给用户，告诉用户
    // 可以将应用添加到桌面，同时可以告知如何操作


})
//end   addEventListener('beforeinstallprompt

