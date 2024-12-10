shell参数编码问题解决

直接使用双引号包含即可。。Urlencode可读性不好

function escapeshellarg(prm) {
return  '"'+prm+'"';
   // return encodeURIComponent(prm)
}

