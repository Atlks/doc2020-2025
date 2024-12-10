Publish npm pkg


 
 


注册NPM账号
项目工程的前期准备结束后, 我们需要去准备npm发布的事宜了.首先就是要去NPM注册账号
邮箱验证
注册好账号后,你所填写的邮箱,会收到一封验证email,这里一定一定要先验证,验证通过后,后面才可以发布npm包.否则会包403或者401的错误!!!

Dev mod
Add package.json....cfg main...
Or just index.js is more easy
进入模块名目录查找 package.json 文件中的 main 配置项，导入该配置项指定的文件
如果模块名目录中没有 package.json文件，或package.json文件中没有 main 配置项，则加载 index.js 文件


项目调试
开发过程中,需要对项目进行调试,这个时候我们可以时候,可以使用npm link来进行调试,具体方式如下
cd 进入包项目根目录, 命令行执行 npm link. 将该项目映射到全局
npm link
cd 进入需要使用这个包的项目的根目录, 执行npm link + package名称 将刚才映射到全局的包装到当前项目的node_modules文件夹.这个时候,你就可以在这个项目中,引用使用你开发的npm包啦. 这里要注意的是,package名称,就是前文提到的,package.json中第一行的name
npm link + package名称
一般来说只要你没有看到报错,就是link成功啦
当你调试结束时,可以通过npm unlink + package名称的方式,删除安装到node_modules的包.记得要删除!!!! 因为这个并不是真正的npm包, 删除之后, 将npm发布后,再通过npm install安装,重新测试没有问题后,才算是真正的结束
npm发布
当你前面的所有事情都做好之后,就进入到npm发布的这一步了 首先,需要登陆一下npm账号,命令行执行:
npm adduser
之后填写你的npm账号和密码

Fabu npm publish

当你登陆成功,npm源也没有问题的时候,你就可以执行
npm publish
如果这个时候,没有看到报错,那么恭喜你,你可以去这里搜索一下你包的名称,你就可以找到你发布的包啦
安装你的npm包
另外创建一个项目,或者使用现成的其他项目.通过执行npm i + 你的包名称 + -S来安装你刚刚发布的npm包吧.安装好后,你可以再次进行测试.



3. 自定义模块查找规则
在当前目录下查找对应的文件
进入同名目录查找package.json文件，在文件中查找main配置项（引入的实际上是配置项指定的文件）
如果没有package.json文件，或者package.json文件中没有main配置项，才去引入 index.js 文件
4. 第三方模块查找规则
在当前目录下查找node_modules目录；如果没有则向上一层目录查找，如果也没有则继续向上层目录查找直到根目录； 如果都没有则报错
进入node_modules中查找模块名目录；如果没有则报错
进入模块名目录查找 package.json 文件中的 main 配置项，导入该配置项指定的文件
如果模块名目录中没有 package.json文件，或package.json文件中没有 main 配置项，则加载 index.js 文件


