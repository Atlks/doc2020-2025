Atitit sql 查询结果 转换为json 输出


使用JSON_OBJECT  推荐
select 'vv' AS `t1`,
JSON_OBJECT('id', 87, 'name', 'carrot') jo

使用 group_concat 配合concat 比较麻烦

select
   'vv' AS `t1`,

   (
      select concat
         (
            '[',
            group_concat
            (
               concat
               (
                  '{"name":"',
                  'aiai',
                  '",'
               ),
               concat
               (
                  '"id":"',
                  55,
                  '"}'
               )
               separator ','
            ),
            ']'
         )
   ) AS `j2`


但是输出貌似都是json str格式不是json模式


{"count":1,"data":[{"t1":"vv","jo":"{\"id\": 87, \"name\": \"carrot\"}","j2":"[{\"name\":\"aiai\",\"id\":\"55\"}]"}],"pageCount":1,"page":"1","pagesize":"10"}

