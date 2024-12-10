Lst lst lst 列表 创新btn bt btn 按钮

Evry 每一个 ctrl 控件can 能 fmt 格式 otpt 输出

Just fmt 格式 otpt 输出 as 作为 btn 按钮 is   ok 



columns = [

   {data: 'uname'},
   {data: 'cashio'},
   {data: 'amt'},
   {data: 'time'},
   {data: 'stat'},
   {
       data: 'time',
       render: function ( data, type, row ) {
           console.log(row)
           window['row'+row.id]=row
           let id=row.id;
           let clkstr="accpt2423('"+id+"')"
           let clkstr_rfs="rfs('"+id+"')"
           return '<button class="accptbtn" onclick='+clkstr+'>通过</button><button  class="accptbtn" onclick='+clkstr_rfs+'>拒绝</button>';
       }
   }
]

console.log(" rzt json str is :" + rzt.substring(0, 250))

rzt2=rzt;
loadToDataTableV2(json_decode(rzt), "tab_oplog", columns, [[4, "desc"]])





function loadToDataTableV2(jsonArr, tabid,columns123,order123) {
   // let table = new DataTable('#'+tabid);
   //  $('#'+tabid).DataTable( {
   //      data: [],
   //      columns: [
   //          { data: 'uname' },
   //          { data: '类型' },
   //          { data: 'score' },
   //          { data: 'time' }
   //      ]
   //  } );

   $.fn.dataTable.ext.errMode = 'none';

   if (window['sxftab224'])
       window['sxftab224'].destroy();

   let dt224 = $('#' + tabid).DataTable({
       data: jsonArr,
       columns:  columns123,
       order:order123,
       buttons: ['colvis', 'excel', 'print'],
       language:{
           "processing": "处理中...",
           "lengthMenu": "显示 _MENU_ 项结果",
           "zeroRecords": "没有匹配结果",
           "info": "显示第 _START_ 至 _END_ 项结果，共 _TOTAL_ 项",
           "infoEmpty": "显示第 0 至 0 项结果，共 0 项",
           "infoFiltered": "(由 _MAX_ 项结果过滤)",
           "infoPostFix": "",
           "search": "搜索:",
           "searchPlaceholder": "搜索...",
           "url": "",
           "emptyTable": "表中数据为空",
           "loadingRecords": "载入中...",
           "infoThousands": ",",
           "paginate": {
               "first": "首页",
               "previous": "上页",
               "next": "下页",
               "last": "末页"
           },
           "aria": {
               "paginate": {
                   "first": "首页",
                   "previous": "上页",
                   "next": "下页",
                   "last": "末页"
               },
               "sortAscending": "以升序排列此列",
               "sortDescending": "以降序排列此列"
           },
           "thousands": "."
       }
   })
   window['sxftab224'] = dt224;
   $("#loaddiv").hide();

}

