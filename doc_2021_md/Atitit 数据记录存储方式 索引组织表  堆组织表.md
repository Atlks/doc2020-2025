Atitit 数据记录存储方式 索引组织表  堆组织表


储方式
InnoDB 引擎把数据放在主键索引上，其他索引上保存的是主键 id。这种方式，我们称之为索引组织表（Index Organizied Table）。
Memory 引擎采用的是把数据单独存放，索引上保存数据位置的数据组织形式，我们称之为堆组织表（Heap Organizied Table）


堆组织表就不说了，其索引中记录了记录所在位置的rowid，查找的时候先找索引，然后再根据索引rowid找到块中的行数据

索引组织表，其行数据以索引形式存放，因此找到索引，就等于找到了行数据。
--
堆组织表的数据是散放的，索引和表的数据是分离的

索引组织表的索引和数据是在一起的


堆表（HOT）和索引组织表（IOT）优缺点– 运维那点事
www.ywnds.com › ...

· Translate this page
1 Aug 2018 — 堆（heap）组织表数据行在堆中存储，没有任何特定顺序，向一个全新的没有做过更新和删除的堆中插入一行时候，总是append 到堆表文件的 ...


堆组织表：
   通常我们默认建的表就是堆组织表。
   语法：Create table test(  
    Id int,  
    Name varchar2(10)  
  );
   此类型的表中，数据会以堆的方式进行管理，增加数据时候，会使用段中找到的第一个能放下
   此数据的自由空间。当从表中删除数据时候，则允许以后的UPDATE和INSERT重用这部分空间，
   它是以一种有些随机的方式使用。
堆组织表（heap organized table）
Oracle中有很多类型的表，像堆组织表、索引组织表、索引聚簇表等等。首先，我将从最基本、最常用的堆组织表（heap organized table）介绍。
通常我们默认建的表就是堆组织表。语法（详细语法请参见Oracle官方文档）如下：




索引组织表(index organized table, IOT)：就是存储在一个索引结构中的表，数据按主键进行存储和排序。
   适用的场景：
    a.完全由主键组成的表。这样的表如果采用堆组织表，则表本身完全是多余的开销，
      因为所有的数据全部同样也保存在索引里，此时，堆表是没用的。
    b.代码查找表。如果你只会通过一个主键来访问一个表，这个表就非常适合实现为IOT.
 c.如果你想保证数据存储在某个位置上，或者希望数据以某种特定的顺序物理存储，IOT就是一种合适的结构。 IOT提供如下的好处：
  ·提高缓冲区缓存效率，因为给定查询在缓存中需要的块更少。
  ·减少缓冲区缓存访问，这会改善可扩缩性。
  ·获取数据的工作总量更少，因为获取数据更快。
  ·每个查询完成的物理I/O更少。
索引组织表
An index-organized table has a storage organization that is a variant of a primary B-tree. Unlike an ordinary (heap-organized) table whose data is stored as an unordered collection (heap), data for an index-organized table is stored in a B-tree index structure in a primary key sorted manner. Besides storing the primary key column values of an index-organized table row, each index entry in the B-tree stores the nonkey column values as well 
索引组织表有一个可变的主B树存储组织。不象普通表(堆组织),数据是无序存储的集合。   
  索引组织表是以主键排序的方式的B树组织结构。  

而iot 就是类似一个全是索引的表，表中的所有字段都放在索引上，所以就等于是约定了数据存放的时候是按照严格规定的，在数据插入以前其实就已经确定了其位置，所以不管插入的先后顺序，它在那个物理上的那个位置与插入的先后顺序无关。这样在进行查询的时候就可以少访问很多blocks，但是插入的时候，速度就比普通的表要慢一些。


3. 索引聚簇表：
   聚簇是指：如果一组表有一些共同的列，则将这样一组表存储在相同的数据库块中；聚簇还表示把相关的数据存储在同一个块上。
   利用聚簇，一个块可能包含多个表 的数据。概念上就是如果两个或多个表经常做链接操作，那么可以把需要的数据预先存储在一起。
   聚簇还可以用于单个表，可以按某个列将数据分组存储。  
   语法：
   索引聚簇表是基于一个索引聚簇（index cluster）创建的。
   里面记录的是各个聚簇键。聚簇键和我们用得做多的索引键不一样，索引键指向的是一行数据，
   聚簇键指向的是一个ORACLE BLOCK。我们可以先通过以下命令创建一个索引簇。
   create cluster emp_dept_cluster
( deptno number(2) )
