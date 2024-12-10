Atitit webview 播放video全屏解决方案

自动横竖屏根据系统自动。。。

增加一个全屏按钮
会自动定时检测屏幕全屏播放
<button onclick="fullscr()">全屏</button>
   <script>
     function fullscr(){
     
       window.setInterval(()=>{
       
       // document.body.clientHeight  会buduan auto heigt more
         var visuht=window.screen.availHeight;
         console.log(document.body.clientWidth+"*"+visuht)
        if (document.body.clientWidth < 500)
        {
          $("#player").height( visuht);
        }
             
         else
         {
          $("#player").width("100%");
      
          $("#player").height(   visuht);
         }     
           
       },500)
     }
   </script>

Webview本身也有方案android的但是太麻烦了。。

推出全屏，只要拉出下面按钮，推出全屏即可
