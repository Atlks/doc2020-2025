编写兼容性强的lib  兼容浏览器和node 和es


使用默认的cms风格，不要es的。。


直接<script>导入node模块到浏览器会报module模块找不到
可以简单判断此变量是否存在即可


if  (isset("module" ) )
module.exports = { substr, console_log,sprintf,startwith,str_replace,strtolower,strlen,strpos,trim,sprintf }






function isset(varname) {
   try {
       varname = trim(varname);
       rzt = typeof (eval(varname));
       return typeof (varname) != "undefined";
   } catch (e) {
       console_log(e.message);
       //  console_log(e);
       return false;
   }

}

