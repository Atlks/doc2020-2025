Comm file fmt


文件格式

 　　配置文件是一种非常基础的文件格式，但远没有

　INI（.ini）文件是一种非常原始的基础形式，但各家有各家的用法，而且它最多只能解决一层嵌套。只适合非常非常简单的配置文件，一旦需要两层嵌套，或需要数组，就力不从心了。


。即便 JSON5（.json5 - ECMAScript 5.1 JSON）这种扩展格式允许了你像写 JavaScript 对象那样书写裸键名、允许尾逗号，并且可以有注释，写多行字符串依然麻烦。

　　终于，TOML（.toml）横空出世。它彻底放弃了括号或缩进的底层原理，而是采取了显式键名链的方式。Ini v2
　　为了方便（同时看起来更清楚——这种读和写的契合非常关键！），你可以指定小节名。妙的是，小节名也是可以链式声明的。


档文件格式（如 Markdown）、
编程语言（如 JavaScript）、
甚至二进制文件格式（如 PNG）需求那么复杂。
数据文件格式文（如 SQLite）、




