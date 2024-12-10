Atitit obj to url params

    function queryParams(params) {  //配置参数
        var temp = {   //这里的键的名字和控制器的变量名必须一直，这边改动，控制器也需要改成一样的
            pageSize: params.pageSize,   //页面大小
            pageIndex: params.pageNumber,  //页码
            sortName: params.sortName,
            sortOrder: params.sortOrder,
         
            startTime: $("#startTime").val(),
            endTime: $("#endTime").val(),
            account: $("#account").val(),
            adminUserAccount:$('#adminUserAccount').val(),
            status: $("#status").val(),
            layerId: $("#layerId").val(),
            ckBankAccount: $("#ckBankAccount").val()
        };
        

       if(params.searchText)
          temp. searchText= '%'+params.searchText+'%';
        var params_ret = Object.entries($.extend({}, temp, {exports: true})).reduce((arr, [k, v]) => arr.concat(encodeURIComponent(k) + '=' + encodeURIComponent(v || '')), []).join('&');
