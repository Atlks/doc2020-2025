Atitit 参数传递的几种模式 ApiParam  RequestParam PathVariable


Parameter Types
OpenAPI 3.0 distinguishes between the following parameter types based on the parameter location. The location is determined by the parameter’s in key, for example, in: query or in: path.
path parameters, such as /users/{id}
query parameters, such as /users?role=admin
header parameters, such as X-MyHeader: Value
cookie parameters, which are passed in the Cookie header, such as Cookie: debug=0; csrftoken=BUSe35dohU3O1MZvDCU

ApiImplicitParam Req模式

@ApiParam，  body json模式
就是用于swagger提供开发者文档，文档中生成的注释内容。
@ApiOperation( value = "编辑公告", notes = "编辑公告", httpMethod = "POST" )
    @RequestMapping( value = "/edit", method = RequestMethod.POST )
    public RequestResult edit(
            @ApiParam(name = "title", value = "公告标题", required = true) @RequestParam("title") String title,
            @ApiParam(name = "content", value = "公告内容", required = true) @RequestParam("content") String content){
 
@RequestParam,是获取前端传递给后端的参数，可以是get方式，也可以是post方式。

其中如果前端传递的参数和后端你接受的参数起的名字字段是一致的可以省略不写，所以@RequestParam("title") String title 也可以直接写@RequestParam String title。
如果不一致一定要完整写，不然获取不到，如下面的bis_key就必须写。
@ApiOperation( value = "编辑公告", notes = "编辑公告", httpMethod = "POST" )
    @RequestMapping( value = "/edit", method = RequestMethod.POST )
    public RequestResult edit(
            @ApiParam(name = "bis_key", value = "bis_key", required = true)@RequestParam("bis_key") String bisKey,
            @ApiParam(name = "title", value = "公告标题", required = true) @RequestParam String title,
            @ApiParam(name = "content", value = "公告内容", required = true)  String content,
 
@PathVariable，是获取get方式，url后面参数，进行参数绑定

@ApiOperation(value = "删除公告", notes = "删除公告", httpMethod = "POST")
    @RequestMapping(value = "/delete/{bisKey}", method = RequestMethod.POST)
    public RequestResult remove(@ApiParam(name = "bisKey", value = "需要删除的公告ids", required = true) @PathVariable String bisKey) {
对于Restful风格

@PatchMapping("api/v1/staff/{id}")
    @ApiOperation(value = "修改staff")
    @ApiImplicitParams(
            ApiImplicitParam(name = TokenSe

