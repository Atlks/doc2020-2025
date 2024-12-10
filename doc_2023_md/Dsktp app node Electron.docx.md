Dsktp app  


安装electron

然后书写js文件启动即可
 C:\w\sdkprj\node_modules\electron\dist\electron.exe   C:\w\sdkprj\agt\dsktp.js


第二种模式，使用package.json模式
然后在终端里输入以下命令来配置你的项目
npm init
 这个主要生成 package.json中修改， 
{
    "name": "sdkprj_app",
    "version": "1.0.0",
    "description": "dscpb",
    "main": "agt/dsktp.js",
    "directories": {
        "lib": "lib",
        "test": "test"
    },
main里面指明了初始js文件





运行     C:\w\sdkprj\node_modules\electron\dist\electron.exe   C:\w\sdkprj


  C:\w\sdkprj\node_modules\electron\dist\electron.exe   C:\w\sdkprj\agt\dsktp.js
