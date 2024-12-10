Web rest api 功能  callrmt


async  function callrmt(req, res)  {

   console.log("req querystr=>" + JSON.stringify(req.query))
   let callfun = req.query.callfun;
   require("../libx/dsl.js")

   callfun = callfun.trim()
   let arr = callfun.split(" ");
   let fun = arr[0]


   //if fun need login ,login
   if (fun=="login")
   {

   }else if (fun!="login" && !req.cookies.agtid) {
       res.send("not_loginex@需要登录")
       return
   } else {
       //cookie login
       //fun!="login" &  req.cookies
       sendLoginVisa(req);
   }


   requirex("../libBiz/" + fun + ".js");
   requirex("../libBiz/" + fun + "Node.js")

   try {
       let promise = await dsl_callFrmUiToBiz(callfun);

       send(promise,res)

   } catch (e) {
       if (e?.httpStatuCode)
           res.status(e?.httpStatuCode)
       // if(e.stack)
       log_errV3(e, arguments)
       res.send( json_encode_Err(e) )
   }

}




// C:\w\sdkprj\node_modules\electron\dist\electron.exe  C:\modyfing\jbbot\zmng\dsktp.js
//  node   libBiz/bzweb.js
//   npm i  electron
//   npm i chalk
//   npm i esm-hook
//    npm i node-fetch
//     node_modules/electron/dist/electron  dsktp.js
const {join} = require("path");

require("../libx/errHdlr")
var cookieParser = require('cookie-parser');

/////------------- stgart web
const express = require('express')
const app_web = express()


let webroot = join(__dirname + "/../", '');
console.log("webrt=>" + webroot)
app_web.use(express.static(webroot))
app_web.use(cookieParser());

// respond with "hello world" when a GET request is made to the homepage
app_web.get('/', (req, res) => {
   res.send('okkk')
})

app_web.get('/about', (req, res) => {
   res.send('about')
})

/**
*
* @param libss
*/
// function requireAutoload(libss) {
//     let arr=libss.split(",")
//     for(let lib of arr)
//     {
//         requirex("./"+lib+".js")
//         requirex("./libx/"+lib+".js")
//         requirex("./libBiz/"+lib+".js")
//     }
// }
function incLibs() {
   require("../libx/incHtm")
   require("../libx/autoload")
   require("../libBiz/searchPlayer")
   requireAutoload("logger,includeXAjaxNode,bzDb,user,sys,addUser,searchPlayer,oplog,ex,httpSync,bizHttp,incHtm,exit,login,qryAgtBal")
   require("../libx/logger")
   require("../libx/dsl")
   require("../libx/api2023jb")
   require("../libBiz/bizHttp.js")
   require("../libBiz/oplog.js")
   require("../libx/err.js")
   require("../libx/crpto.js")
   require("../libx/api2023jb.js")
   const fs = require("fs");
   require("../libx/fp_ati1990");
   require("../libx/errHdlr");
   require("../libx/logger")
   global["reg"] = reg;
   global["login"] = login;
   require("../libx/php.js")
   require("../libBiz/acc.js")
   require("../libx/ref.js")
   require("../libx/sys.js")
   require("../libx/enc.js")
   require("../libBiz/bizErr.js")

   require("../libx/aes.js")
   require("../libBiz/bizHttp.js")
   require("../libBiz/shangfen.js");
   require("../libBiz/shangfenNode.js")
}

incLibs()

function requirex(f) {
   try {
       console.log(f)
       require(f)
   } catch (e) {
       console.warn(e.message)
   }

}

function send(retTxt,res) {
   if (typeof retTxt == "string")
       res.send((retTxt))
   else if (typeof retTxt != "string")
       res.send(JSON.stringify(retTxt))
}

function sendLoginVisa(req) {
   visa = {"agtid": req.cookies.agtid, "desCode": req.cookies.desCode, "md5Code": req.cookies.md5Code}
   global['visa'] = visa
   global['agtid'] = req.cookies.agtid
   global['agentid'] = req.cookies.agtid

   global['desCode'] = req.cookies.desCode
   global['md5Code'] = req.cookies.md5Code
}

/**
* http://localhost:8000/api?callfun=player_kick 777
*/
app_web.get('/api', async (req, res) => {

   console.log("req querystr=>" + JSON.stringify(req.query))
   let callfun = req.query.callfun;
   require("../libx/dsl.js")

   callfun = callfun.trim()
   let arr = callfun.split(" ");
   let fun = arr[0]


   //if fun need login ,login
   if (fun=="login")
   {

   }else if (fun!="login" && !req.cookies.agtid) {
       res.send("not_loginex@需要登录")
       return
   } else {
       //cookie login
       //fun!="login" &  req.cookies
       sendLoginVisa(req);
   }


   requirex("../libBiz/" + fun + ".js");
   requirex("../libBiz/" + fun + "Node.js")

   try {
       let promise = await dsl_callFrmUiToBiz(callfun);

       send(promise,res)

   } catch (e) {
       if (e?.httpStatuCode)
           res.status(e?.httpStatuCode)
       // if(e.stack)
       log_errV3(e, arguments)
       res.send( json_encode_Err(e) )
   }

})

app_web.get('/tmot', (req, res) => {

   setTimeout(() => {


       res.send('tmot')
   }, 15000)

})


console.log(77)

var server = app_web.listen(8000, function () {

   var host = server.address().address
   var port = server.address().port

   console.log("应用实例，访问地址为 http://localhost:%s", host, port)

})

console.log(999999)



app_web.get('/api', async (req, res) => {

   console.log("req querystr=>" + JSON.stringify(req.query))
   let callfun = req.query.callfun;
   require("../libx/dsl.js")

   callfun = callfun.trim()
   let arr = callfun.split(" ");
   let fun = arr[0]

   if (fun=="login")
   {

   }else if (fun!="login" && !req.cookies.agtid) {
       res.send("not_loginex@需要登录")
       return
   } else {
       //fun!="login" &  req.cookies
       visa = {"agtid": req.cookies.agtid, "desCode": req.cookies.desCode, "md5Code": req.cookies.md5Code}
       global['visa'] = visa
       global['agtid'] = req.cookies.agtid
       global['agentid'] = req.cookies.agtid

       global['desCode'] = req.cookies.desCode
       global['md5Code'] = req.cookies.md5Code
   }


   requirex("../libBiz/" + fun + ".js");
   requirex("../libBiz/" + fun + "Node.js")

   try {
       let promise = await dsl_callFrmUiToBiz(callfun);

       if (typeof promise == "string")
           res.send((promise))
       else if (typeof promise != "string")
           res.send(JSON.stringify(promise))
   } catch (e) {
       if (e?.httpStatuCode)
           res.status(e?.httpStatuCode)
       // if(e.stack)

       log_errV3(e, arguments)


       res.send( json_encode_Err(e) )
   }

})

