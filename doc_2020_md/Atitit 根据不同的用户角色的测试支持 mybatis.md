Atitit 根据不同的用户角色的测试支持 mybatis



应该原则  可以在测试时候指定不同的用户名与角色。。

每个角色use diff unit test


Unit


public void manAddInhwe() throws Exception {

    RequestImpAdv ri = new RequestImpAdv();
    ri.setParam("dbg_normallogin", "normal");
 //   ri.setParam("process_name", "上报隐患流程");


    Processor pcr = new Processor();
    pcr.req = ri;
    String rzt = pcr.startProcess("上报隐患流程");
    try { 


Login user info ret by mybatis

<select id="listRecentlyLoginUsrMood" parameterType="map" resultType="map">
  <!-- loginUserInfo.role_id  -->

    <if test="dbg_pmclogin != null">
       select 'pmcadmin' as role_id,'uidxx' uid
    </if>


    <choose>
        <when test="dbg_mainlogin != null">
            select 'mainadmin' as role_id,'uidxx' uid
        </when>
        <when test="dbg_adminlogin != null">
            select 'gwh' as role_id,'uidxx' uid
        </when>
        <when test="dbg_normallogin != null">
            select 'pmcnormal' as role_id,'uidxx' uid,'uacc' acc
        </when>


        <otherwise>
            select * from  onlineUser where tkid=#{tkid}
        </otherwise>
    </choose>

  </select>

