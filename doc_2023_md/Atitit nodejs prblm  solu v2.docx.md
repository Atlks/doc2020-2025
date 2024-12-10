Atitit nodejs prblm  solu

http lib   node fetch better...syncreq not good
兼容浏览器 模块导出 检测module变量是否存在
if (isset("module"))
   module.exports = {call_user_func,isset,time,echo,substr, console_log, sprintf, startwith, str_replace, strtolower, strlen, strpos, trim, sprintf}


Need export too many namevar to export fun..use glb bind fun
require( './php.js')
echo(999)

利用glb对象把fun绑定到glb属性上，外面可以直接使用。。

global["time"]=time;
global["echo"]=echo;
function trim(str) {
   return str.trim();
}

Node fetch cant use in cjs

require("esm-hook");
const fetch = require('node-fetch').default

Cmd output mlutiline how to read..于dbg信息区分开  使用隔离字符串区分即可，类似html upld的处理

 const {exec, execSync} = require('child_process');
   cmd = "node    "+__dirname+"/libx/callFun.js   "+cmdstr;
// cmd = "electron    "+__dirname+"/libx/callFun.js reg "+uname +" pwd "+ nickname ;


   console.log("cmd=>"+cmd)
   rzt=execSync(cmd).toString();
    rzt=rzt.split("88888888888888888888888888").pop();
   console.log("[dsl_callFunCmdMode] rzt=>" + rzt)

Cantdbug in vs
Launch.jsn
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Launch Program",
            "program": "${file}",
            "request": "launch",
           
            "type": "node"
        },
        

And  enble  node debug ext..


同步依赖类库  package.json
使用npm install即可。。。


The V8 platform used by this instance of Node does not support creating Workers
Electron cant invk js fun...just need use ipc or cli web api to ivk
