Atitit 纯java项目的提升进度大法---通用json dsl接口

1. Json dsl接口	1
1.1. Url：  http://aaa.com/api_jsondsl?dsl={}	1
1.2. 参数为json对象，具体字段如下	1
1.3. 返回 ：json数组。	2
2. 范例：查询用户数据	2
2.1. 增加数据	2
2.2. 修改数据	3

Json dsl接口
Url：  http://aaa.com/api_jsondsl?dsl={}

参数为json对象，具体字段如下


返回 ：json数组。

范例：查询用户数据
http://aaa.com/api_jsondsl?dsl= {
    "操作": "查询", 
    "数据类型": "用户数据", 
    "查询属性": "用户名,年龄,电话", 
    "条件": "用户名='王伟' and  电话='1356666666'", 
    "数据排序依据字段": "电话,用户名 倒排", 
    "页数": 2, 
    "每页条数": 10
}

注意：dsl参数需要urlencode，这里为了可读性暂时不编码
增加数据
http://aaa.com/api_jsondsl?dsl= {
    "操作": "添加数据", 
    "数据类型": "用户数据", 
    "内容": [        {
            "用户名": "王伟", 
            "电话": "123"
        },         {
            "用户名": "李三", 
            "电话": "456"
        }
    ]
}
修改数据
http://aaa.com/api_jsondsl?dsl= {
    "操作": "修改数据", 
    "数据类型": "用户数据", 
    "内容": [        {
            "用户名": "王伟", 
            "电话": "123"
        },         {
            "用户名": "李三", 
            "电话": "456"
        }
],
    "条件": "id=34"
}



前段见面调用


<textarea  id="txt" style="width:700px;height:700px" ></textarea>
<meta http-equiv=Content-Type content="text/html; charset=gbk">
<script>

function 按照(col)
{

return {
	倒排:function(){return  col+" desc" }
};
}


发送参数={};
发送参数.操作="查询"
发送参数.数据类型="用户数据"
发送参数.查询属性="用户名,年龄,电话";
发送参数.条件="用户名='王伟' and  电话='1356666666'";
发送参数.数据排序依据字段="用户名 倒排"
发送参数.页数=2;
发送参数.每页记录数=10;

 //document.getElementById('txt').value=JSON.stringify(发送参数); 

 
 发送参数={};
发送参数.操作="添加数据"
发送参数.数据类型="用户数据"
 
发送参数.内容=[];
发送参数.内容.push({});
发送参数.内容[0].用户名="王伟";
发送参数.内容[0].电话="123";
发送参数.内容.push({});
发送参数.内容[1].用户名="李三";
发送参数.内容[1].电话="456";
 
//document.getElementById('txt').value=JSON.stringify(发送参数); 



 发送参数={};
发送参数.操作="修改数据"
发送参数.数据类型="用户数据"
 
发送参数.内容=[];
发送参数.内容.push({});
发送参数.内容[0].用户名="王伟";
发送参数.内容[0].电话="123";
发送参数.内容.push({});
发送参数.内容[1].用户名="李三";
发送参数.内容[1].电话="456";
 发送参数.条件="id=34"
document.getElementById('txt').value=JSON.stringify(发送参数); 

</script>


作者:: 绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher  kok  虔诚者Pious 宗教信仰捍卫者 Defender Of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak 万兽之王
简称：： Emir Attilax Akbar 埃米尔 阿提拉克斯 阿克巴
全名：：Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 埃米尔 阿提拉克斯 阿克巴 本 马哈茂德 本 阿提拉 本 所罗门 本亚当  阿尔 拉帕努伊
常用名：atl（ail），  EMAIL:1466519819@qq.com
 
 
头衔：uke总部o2o负责人，全球网格化项目创始人，
uke交友协会会长  uke捕猎协会会长 Emir Uke部落首席大酋长，
 
uke宗教与文化融合事务部部长， uke宗教改革委员会副主席
uke制度与重大会议委员会委员长，uke保安部首席大队长,uke制度检查委员会副会长，
 
uke 首席cto   软件部门总监 技术部副总监  研发部门总监主管  产品部副经理 项目部副经理   uke科技研究院院长uke软件培训大师
 
uke波利尼西亚区大区连锁负责人 汤加王国区域负责人 uke克尔格伦群岛区连锁负责人，莱恩群岛区连锁负责人，uke布维岛和南乔治亚和南桑威奇群岛大区连锁负责人
 Uke软件标准化协会理事长理事长 Uke 数据库与存储标准化协会副会长
 
uke终身教育学校副校长   Uke医院 与医学院方面的创始人
 uec学院校长， uecip图像处理机器视觉专业系主任   uke文档检索专业系主任
Uke图像处理与机器视觉学院首席院长
Uke 户外运动协会理事长  度假村首席大村长   uke出版社编辑总编
 
转载请注明来源：attilax的专栏  ?http://blog.csdn.net/attilax
--Atiend  v8

