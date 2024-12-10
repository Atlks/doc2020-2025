Err ex prcs bpx

Throw ex use str mode more easy
Dont need oo....new ex class...

dafjadfEx@errcode@msg
notLoginEx@notLoginCode@没有登录
分别catch



Throw ex

function authChk() {
   log_fun_enter(arguments)

   let f = process.env.USERPROFILE + "/lgky.json"
   let obj = readFileAsJson(f);

   console.log(obj)
   console.log("[8authChk ]agentid:" + obj.agentid)


   if (isLogin()) {
       set_login_token(obj)
   } else
       throw "not_loginex@没有agtid,需要登录"



try {
   authChk()
   console.log("[user_ini_ui] logined..")
   $("#unameLab").text(agentid);//show lab
   $("form").hide();
   $("#loginFm").hide();
   $("#logined").show();

} catch (e) {


   catchHdl(e, "not_loginex", function () {
       console.log(e.split("@")[1])
       //  console.log(e)
       console.log("[ ] not login  ")
       $("form").show();
       $("#logined").hide();

   })




function catchHdl(e, extype, catchFun) {

   if (typeof e === 'string') {
       if (e.startsWith(extype)) {
           catchFun();

       } else {
           throw e;
       }

   } else
       throw e;

}

