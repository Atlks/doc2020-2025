User sys argo 用户系统算法



注册算法


登录算法


/**
* 登录流程
* @param 用户名
* @param 密码
*/
function 登录流程(用户名, 密码) {


   检查结果=检查用户名密码( 用户名,密码);
   如果(检查通过(检查结果),
       发放登录凭据(用户名 ),
       显示退出按钮区域, 关闭登录区域, 转到主界面,
       添加操作日志("用户 (@用户名@)登录，时间 @当前时间@")
   )

   如果(检查不通过(检查结果) , 提示("用户名密码不对"), 终止流程 )


}





发放登录凭据
function 发放登录凭据(用户名) {

   过期日=计算过期日("@当前日期@+7")
    return ()=>{

        console.log("发放登录凭据....")
        var 登录凭据 = {"用户名": 用户名, "过期日": 过期日};
        登录凭据.加密效验码 = md5(用户名 + 过期日)
        保存登录凭据(登录凭据)
    }

}



登录凭据检测 authChk   throwEx

function authChk() {
   log_fun_enter(arguments)


   let obj =  getLoginToken()
 //  alert(obj)
   if(!obj)
       throw "cant find visa Ex@没有agtid,需要登录"


isLogin

function isLogin() {
   log_fun_enter(arguments)

   let obj =getLoginToken()

   console.log("[8authChk ]agentid:" + obj.agentid)
   if (obj.agtid) {
       set_login_token(obj)
       return true
   } else {
       return false;
   }
}

