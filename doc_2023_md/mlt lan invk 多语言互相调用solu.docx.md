多语言互相调用solu

Exec( shell )  需要进行shell参数编码，俩边增加双引号即可。

Execfile 这种更加好，无需进行参数编码，更加简单使用方便。。
Execfile (php.exe  xxx.php arg )  


function execFil(execFile, args) {

   const {execFileSync, exec, execSync} = require('child_process');

   $rzt = execFileSync(execFile, args, {
       encoding: "utf-8",
       windowsHide: true,
       cwd: process.cwd(),
       timeout: 5000,
       maxBuffer: 10 * 1024 * 1024,
       shell:false
   })

   let message = $rzt.toString();
   message = message.trim()

   console.log(message)
   return message;
}

