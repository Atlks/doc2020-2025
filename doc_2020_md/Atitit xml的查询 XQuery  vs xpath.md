Atitit xml的查询 XQuery  vs xpath

解释XQuery 最佳方式是这样讲：XQuery 相对于XML 的关系，等同于SQL 相对于数据库表的关系。 XQuery 被设计用来查询XML 数据- 不仅仅限于XML 文件，还包括任何可以XML 形态呈现的数据，包括数据库。


看看 XQuery
XPath 无疑非常强大，但也有其局限性。最突出的是，它很大程度上只适合静态数据。换句话说，需要针对特定文档编写 XPath 查询，提供和元素、属性、文本比较的具体数据来使用谓词和 XPath。此外，XPath 也没有任何控制结构（如 if/else 语句），除了简单的比较外也不能执行任何处理。
坦白地说，这些限制对多数非程序员来说算不上大问题。但是对于 Java（或者 C#、Python）程序员，习惯了完整的编程语言的强大功能，很快就想到需要 XPath 本身功能之外的方法搜索 XML 文档。于是 XQuery 理所当然地登场了。
XQuery 和 FLWOR
当然除了简单地文档选择外，XQuery 还提供了更多的功能。它的 FLWOR 功能尤为强大。FLWOR 是 “for、let、where、order by、return” 的缩写。这都是可用于 XQuery 表达式以便得到更精确结果的子句。
不是 flower
不清楚创造这个缩写词的人为何选择 FLWOR 而不是 FLOWR，第一个没法拼读，第二个看起来像 “flower”。原因很明显，多数表达式中子句的顺序是 for、where、order by 和 return。但还剩下 let，它可以出现在 XQuery 之前或之中。
缩写为 FLWOR 是因为标准化 XML 规范的小组（W3C）选择了它，不过最好不要使用 FLOWR 以免在其他熟悉 XML 的朋友面前丢脸。
对于 SQL 老手来说，应该感到有些熟悉了。 WHERE 和 ORDER BY 都是 SQL 查询中常见的部分。对于程序员来说， for 应该比较眼熟。下面是关于 FLWOR 子句的简要说明：
for：使用 for 遍历节点集。在很多方面，for 就将节点集的当前值赋给变量从而操作该变量。
let：使用 let 可以为变量赋值，但是（很快将看到）和其他 FLWOR 子句相比，let 用的比较少。
where：where 允许向节点集应用选择条件，除了 XPath 原有的机制意外。当然，您将看到在很多查询中 where 并不比 XPath 强，只不过把 XPath 的谓词转移了一个地方。
order by：order by 子句不改变或者筛选数据，仅用于排序结果集，XPath 只能按位置排序，该子句允许按照其他数据排序。
return：使用 return 子句允许您操作操作节点集，随后返回除该节点集以外的结果。有可能在选择节点集、排序并筛选之后，只返回结果的子元素，return 是实现这种功能的关键。

