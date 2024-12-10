Atitit mybatis springboot 结合使用








//  http://localhost:8088/executeQuery?select_id=warning_query
    @ApiOperation(value = "执行查询操作 通过接口", notes = "请求数据说明note")
    @RequestMapping(value = "/executeQuery")
    @ResponseBody
    public String executeQuery(String select_id) throws Exception {
        ResponseUtil.setAccessControlAllowOrigin(res);//setAccessControlAllowOrigin();
    //    com.github.pagehelper.PageInterceptor
        try {
            PageInfo pageInfo=  MybatisUtil.executeQuery(select_id);
            return (JSON.toJSONString(pageInfo,true));

        } catch (Exception e) {
            return ExceptionUtil. getEx(e);
        }
        //throw new RuntimeException("not imp");
    }

