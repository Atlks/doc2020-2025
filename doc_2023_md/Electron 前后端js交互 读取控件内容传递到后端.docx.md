Electron 前后端js交互 读取控件内容传递到后端

设置  contextIsolation: false



 const { app, BrowserWindow } = require('electron')

 function createWindow() {
     // 创建浏览器窗口
     const win = new BrowserWindow({
         width: 800,
         height: 600,
         webPreferences: {
             nodeIntegration: true,
             contextIsolation: false
         }
     })

     // 并且为你的应用加载index.html
     win.loadFile('index.html')
     win.openDevTools();

 }

 // Electron会在初始化完成并且准备好创建浏览器窗口时调用这个方法
 // 部分 API 在 ready 事件触发后才能使用。
 app.whenReady().then(createWindow)


这样端加载的js也能调用后端js node类库了。。


function clk() {
    document.getElementById("fname").value = 111;
    console.log(1111111111111111)

    writeFileSyncx("43200x.txt", "999");
}

function writeFileSyncx(fil, str) {
    var fs = require("fs");
    var path = require("path");
    fs.mkdirSync(path.dirname(fil), { recursive: true });
    //   fs.mkdirSync(appRoot + '/css

    fs.writeFileSync(fil, str);
}

