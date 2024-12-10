Node js upload updt原理

读取req数据，生成对象。。
可以直接读取txt

大文件需要读取tmp文件比较好

function readFileFromUploadFile(req)


·  express-fileupload - 用于上传文件的简单的 Express 中间件。它可以解析 multipart/form-data 请求, 如果有文件的话会提取文件并且使其可通过 req.files 属性访问。
·  morgan - 用于记录HTTP请求日志的 Node.js 中间件。
·  lodash - 一个提供数组、数字、对象、字符的工具函数的 JavaScript 库。


[NodeJS] 使用Express multer搭建文件上传服务原创

CSDN博客
https://blog.csdn.net › details

Apr 14, 2022 — multer是express官方推荐的文件上传中间件，它是在busboy的基础上开发的。目前multer的最新版本为：~...本文将详细介绍express文件上传中间件Multer的安装 ..

在开发的过程中，为了方便每次保存之后系统都自动更新，添加 nodemon 用于支持热更新

express框架的基本服务就算起来了，为了方便开发和调试，在package.json文件中script部分加上这么一条
"dev": "nodemon ./bin/www"
然后使用 npm run dev 命令来启动服务就可以实现服务的热更新了
er中实现上传的功能，下方代码实现的是单文件上传，其中上传文件是，需要body中有一个字段叫file(可自定义)。 在req.files中的文件是经过express-fileupload处理的，它是一个对象，每一对象都是一个封装了了文件实例，实例中有一个mv方法，用于保存文件。



   //-----------------------------fileupdt
   // 引入express-fileuplod
   var fileUpload = require('express-fileupload');
// 使用express-fileupload中间件
   app_web.use(fileUpload());
   //-----------------------------fileupdt end



req=global['req'];
let avatar = req.files.file1;

//Use the mv() method to place the file in upload directory (i.e. "uploads")
// avatar.mv('./uploads/' + avatar.name)
let t = avatar.data.toString();
   //readFileSyncx(avatar)





function uploadIni(app_web) {
   //-----------------------------fileupdt
   // 引入express-fileuplod
   var fileUpload = require('express-fileupload');
// 使用express-fileupload中间件
   app_web.use(fileUpload());
   //-----------------------------fileupdt end
}



function importUser(file) {

   req = global['req'];
   let t = readFileFromUploadFile(req);



function readFileFromUploadFile(req) {
   let avatar = req.files.file1;

   //Use the mv() method to place the file in upload directory (i.e. "uploads")
   // avatar.mv('./uploads/' + avatar.name)
   let t = avatar.data.toString();
   return t;
}

