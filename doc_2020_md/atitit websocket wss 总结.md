Java的资料太少了，php和js的很多

主要原理是增加一个ssl证书

浏览器测试需要先访问下https自动把证书保存下来，在连接wss就可以了。

const WebSocket = require('ws');
 
// npm install ws 
// npm install openssl-self-signed-certificate 
// node /data/ws.js
var https = require('https');
var selfSigned = require('openssl-self-signed-certificate');

var options = {
    key: selfSigned.key,
    cert: selfSigned.cert
};
console.log(options);

// 创建request请求监听器
const processRequest = (req, res) => {
    res.writeHead(200);
    res.end('ok,u r already receive cert,u can test WebSockets!\n');
};

const server = https.createServer(options,processRequest).listen(8888);
//console.log(`HTTPS started on port ${port + 1} (dev only).`);
const wss = new WebSocket.Server({ server });

global.conns = new Array();
 // {method:"testsend",msg:{"aa":1111}}
wss.on('connection', function connection(ws) {
  global.conns.push(ws);
  ws.on('message', function incoming(message) {
    console.log('received: %s', message);
      try{
        var json = eval('(' + message + ')');
        if (json.method=="testsend")
        {
          global.conns .forEach((wsConn, i) => 
              {
           //     console.log(v);
                try{

                  var retstr=JSON.stringify(  json.msg); 
                  console.log('conns .forEach send:'+ retstr);
                  wsConn.send(retstr);
                }catch(e){
                  wsConn.send('except:'+ e);
                }
               
                
              }  
          );
          //end foreach

       
        }
        else
        throw "cant find method ";
     
       
      }catch(e)
      {
        ws.send('except:'+ e);
      }
  
  });
 
  ws.send('conn ok');
});
console.log("fff")

