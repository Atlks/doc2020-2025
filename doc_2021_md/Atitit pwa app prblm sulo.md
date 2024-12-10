Atitit pwa app prblm sulo


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

