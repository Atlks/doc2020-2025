Atitit btree 搜索原理


左边小右边大 的有序树


       B树的搜索，从根结点开始，如果查询的关键字与结点的关键字相等，那么就命中；否则，如果查询关键字比结点关键字小，就进入左儿子；如果比结点关键字大，就进入右儿子；如果左儿子或右儿子的指针为空，则报告找不到相应的关键字；
平衡算法
但B树在经过多次插入与删除后，有可能导致不同的结构：

   右边也是一个B树，但它的搜索性能已经是线性的了；同样的关键字集合有可能导致不同的树结构索引；所以，使用B树还要考虑尽可能让B树保持左图的结构，和避免右图的结构，也就是所谓的“平衡”问题；      
       实际使用的B树都是在原B树的基础上加上平衡算法，即“平衡二叉树”；如何保持B树结点分布均匀的平衡算法是平衡二叉树的关键；平衡算法是一种在B树中插入和删除结点的策略；
小结
       B树：二叉树，每个结点只存储一个关键字，等于则命中，小于走左结点，大于走右结点；
       B-树：多路搜索树，每个结点存储M/2到M个关键字，非叶子结点存储指向关键字范围的子结点；
       所有关键字在整颗树中出现，且只出现一次，非叶子结点可以命中；
       B+树：在B-树基础上，为叶子结点增加链表指针，所有关键字都在叶子结点中出现，非叶子结点作为叶子结点的索引；B+树总是到叶子结点才命中；
       B*树：在B+树基础上，为非叶子结点也增加链表指针，将结点的最低利用率从1/2提高到2/3；

层次高度一般3--4层
类似索引
Es的用的
倒排索引，是否真的比B-tree 索引更
当我们不需要支持「快速的更新」的时候，可以用「预先排序」等方式：
换取更小的存储空间
更快的检索速度等好处，
其代价：就是更新慢
ElasticSearch：时间复杂度接近 O(1)，采用「字典树 + 内存存储」
倒排索引：有序的数据字典，根据 field 定位到数据，查找 field 时间复杂度也是 O(logN)
term-index：字典树结构 + 内存存储，快速定位到磁盘的 offset，定位到数据，时间复杂度接近 O(1)，实际为 O(m)，其中 m 为关键字的字符数量
MySQL： B+ 树结构存储，时间复杂度 O(logN)
B+树：按照 B+ 树结构存储，时间复杂度 O(logN)，每次查询都可能经过多次「寻轨」，单次耗时 3~5 ms



，二叉树查找效率是logN，同时插入新的节点不必移动全部节点，所以用树型结构存储索引，能同时兼顾插入和查询的性能。


什么是倒排索引?

Alt text
继续上面的例子，假设有这么几条数据(为了简单，去掉about, interests这两个field):
ID是Elasticsearch自建的文档id，那么Elasticsearch建立的索引如下:
Name:
Age:
Sex:
Posting List
Elasticsearch分别为每个field都建立了一个倒排索引，Kate, John, 24, Female这些叫term，而[1,2]就是Posting List。Posting list就是一个int的数组，存储了所有符合某个term的文档id。
看到这里，不要认为就结束了，精彩的部分才刚开始…
通过posting list这种索引方式似乎可以很快进行查找，比如要找age=24的同学，爱回答问题的小明马上就举手回答：我知道，id是1，2的同学。但是，如果这里有上千万的记录呢？如果是想通过name来查找呢？
Term Dictionary
Elasticsearch为了能快速找到某个term，将所有的term排个序，二分法查找term，logN的查找效率，就像通过字典查找一样，这就是Term Dictionary。现在再看起来，似乎和传统数据库通过B-Tree的方式类似啊，为什么说比B-Tree的查询快呢？


ES索引原理 - 简书
笼统的来说，b-tree 索引是为写入优化的索引结构。所以当我们不需要支持快速的更新的时候，可以用预先排序等方式换取更小的存储空间，更快的检索速度等好处，其代价就是更新慢。要进一步深入的化，还是要看一下 Lucene 的倒排索引是怎么构成的。
Ref
BTree,B-Tree,B+Tree,B_Tree都是什么 - andyzhaojianhui的专栏 - CSDN博客.mhtml

