Atitit  验证 数字验证 非空验证的最佳算法  h5


  <td><select class="searchBox-select"   style="height:25px;" id2="branch_id" id="objid" name="objid" required  >
            <option value="">--物品</option>
            <option  v-for="(dataItem,index) in list_data_obj" v-bind:value="dataItem.clothes_no">{{dataItem.clothes_title}}</option>
          </select></td>
        </tr>
        <tr>
          <td>单价</td>
          <td>
            <input   name="price" id="price" type="number"   min="1" max="1000" /></td>
        </tr>
        <tr>
          <td>&nbsp;</td>
          <td><input type="submit" name="button2" id="button2" value="提交" /></td>
        </tr>

验证非空使用required  
验证数字input type为number即可。。

按钮是sumbit类型的。。。



要转化为ajax，在onsubmit上返回false。。。


HTML5自带的表单验证 - Web 技术研究所.html


作者:: 绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher  kok  虔诚者Pious 宗教信仰捍卫者 Defender Of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak 万兽之王
简称：： Emir Attilax Akbar 埃米尔 阿提拉克斯 阿克巴
全名：：Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 埃米尔 阿提拉克斯 阿克巴 本 马哈茂德 本 阿提拉 本 所罗门 本亚当  阿尔 拉帕努伊
常用名：atl（ail），  EMAIL:1466519819@qq.com


头衔：uke总部o2o负责人，全球网格化项目创始人，
uke交友协会会长  uke捕猎协会会长 Emir Uke部落首席大酋长，

uke宗教与文化融合事务部部长， uke宗教改革委员会副主席
uke制度与重大会议委员会委员长，uke保安部首席大队长,uke制度检查委员会副会长， 

uke 首席cto   软件部门总监 技术部副总监  研发部门总监主管  产品部副经理 项目部副经理   uke科技研究院院长 uke软件培训大师

uke波利尼西亚区大区连锁负责人 汤加王国区域负责人 uke克尔格伦群岛区连锁负责人，莱恩群岛区连锁负责人，uke布维岛和南乔治亚和南桑威奇群岛大区连锁负责人 
 Uke软件标准化协会理事长理事长 Uke 数据库与存储标准化协会副会长 
 
uke终身教育学校副校长   Uke医院 与医学院方面的创始人
 uec学院校长， uecip图像处理机器视觉专业系主任   uke文档检索专业系主任
Uke图像处理与机器视觉学院首席院长
Uke 户外运动协会理事长  度假村首席大村长   uke出版社编辑总编

转载请注明来源：attilax的专栏  ?http://blog.csdn.net/attilax
--Atiend  v8


