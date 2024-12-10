Loading fun

Bootstrop  Loading  plugin



<link rel="stylesheet" href="https://cdn.staticfile.org/twitter-bootstrap/4.3.1/css/bootstrap.min.css">
<script src="https://cdn.staticfile.org/jquery/3.2.1/jquery.min.js"></script>
<script src="https://cdn.staticfile.org/popper.js/1.15.0/umd/popper.min.js"></script>
<script src="https://cdn.staticfile.org/twitter-bootstrap/4.3.1/js/bootstrap.min.js"></script>




<button class="btn btn-primary" disabled id="loaddiv" style="xdisplay:none ">
   <span class="spinner-border spinner-border-sm"></span>
   Loading..
</button>



<script
$("#loaddiv").hide();

function  agtbal648()
{
      $("#loaddiv").show()
 
   setTimeout(function (){

      rzt=  dsl_callFunCmdMode("agtBal" )

               $("#loaddiv").hide();
        alert("此代理余额为:"+rztobj.data.score)


   },100)

