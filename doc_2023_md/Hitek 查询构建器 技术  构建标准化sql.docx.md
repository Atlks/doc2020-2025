Hitek 查询构建器 技术  构建标准化sql
查询构建器
尽管业界在 20世纪 80年代中期就确立了 ANSI 和 ISO SQL 标准。不过直到现在，大多数数据库用的仍然是自己的 SQL 方言。但 PostgreSQL 是个例外，它遵循了 SQL:2008 标准。查询构建器能在支持多种数据库的同时消除各种 SQL 方言的差异，提供一个统一的 SQL 生成接口。对于经常要在不同的数据库技术之间进行切换的团队来说，查询构建器提供的好处不言而喻。
Knex
很多开发人员不喜欢把 SQL 直接放在代码里，希望有一个抽象层隔离一下。因为用字符串拼接 SQL 语句太繁琐了，而且查询可能会变得越来越难以理解和维护。对于 JavaScript 来说更是如此，因为在 ES6 模板常量出来之前，它连表示多行字符串的语法都没有。
Knex是一个轻便的 SQL 抽象包，它被称为查询构建器。我们可以通过查询构建器的声明式 API 构造出 SQL 字符串，Knex 的 API 简单直白：
knex({ client:'mysql'})
	.select()
	.from('users')
	.where({ id:'123'})
	,toSQL();


