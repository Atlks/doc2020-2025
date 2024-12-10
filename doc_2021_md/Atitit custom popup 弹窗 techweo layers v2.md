Atitit custom popup 弹窗 techweo layers

Custom div


<!-- pwa add2dsktp tips -->
<script src="/js\layer-v3.5.1\layer\layer.js"></script>
<div id="tips88" style="padding: 10px;display: none">
    <table width="100%">
        <tr><td width="70">  <img  style="border-radius: 9px;" src="/images/logo.png" width="60" height="60"></td><td style="padding: 7px;">将 添加到手机桌面<br> 随时随地想看就看<br> hxc.one</td></tr>
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




Open

index88 =  layer.open({
    type: 1,title:'',  time: 12000,
    area: ['370px', '140px'],
    end: function () {
        //无论是确认还是取消，只要层被销毁了，end都会执行，不携带任何参数。layer.open关闭事件
        $("#tips88").hide();
    },
    content: $('#tips88') //这里content是一个DOM，注意：最好该元素要存放在body最外层，否则可能被其它的相对元素所影响
});

关闭popup
function  closeLayer(){
    layer.close(index88)
}

关闭事件

   end: function () {
