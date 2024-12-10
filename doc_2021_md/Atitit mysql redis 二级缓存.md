Atitit mysql redis 二级缓存


实体实现序列化接口

Mapper
@CacheNamespace(size = 3000,implementation =RedisCache2JdsV2.class)
//@CacheNamespaceRef(value = null)
public interface CompanyMapper extends Mapper<Company> {
}


也可以使用官方对mybatis-redis cache实现。。  mbtsrds kch





Uese rds cache..debug log,cant show hit cache again..but not output sql ,,so it shuold use reds cache...







   @Override
    public void putObject(Object key, Object value) {
        try {
        	 jds.setex(key.toString(), 600,  JSON.toJSONString(value));
        	 logger.info( "putobj:"+id.toString());
        	 logger.info(" value:"+JSON.toJSONString(value));
        	  jds.setex(key.toString().concat("Bytemode").getBytes(), 600,   SerializeUtil.serialize(value));
        	  
        	   jds.hset(id.toString().getBytes(), key.toString().getBytes(), SerializeUtil.serialize(value));
        	 
//        	if(value instanceof String)
//         jds.setex(key.toString(), 600, value.toString());
//        	else
//        		
        //	jds.set(key, value, EXPIRE_TIME_IN_MINUTES, TimeUnit.MINUTES);
        	// NX是不存在时才set， XX是存在时才set， EX是秒，PX是毫秒
        //	jedisClient.set(key, value, "NX", "EX", expireSecond);
            logger.debug("Put query result to redis");
        } catch (Throwable t) {
            logger.error("Redis put failed", t);
        }
    }

    /**
     * Get cached query result from redis
     *
     * @param key
     * @return
     */
    @Override
    public Object getObject(Object key) {
        try {
//            RedisTemplate redisTemplate = getRedisTemplate();
//            ValueOperations opsForValue = redisTemplate.opsForValue();
//            opsForValue.set(key, value, timeout, unit);
        	
            logger.debug("Get cached query result from redis");
            logger.info( "getObject:"+id.toString());   // getObject:application.dao.CompanyMapper
           Object o=SerializeUtil.unserialize(jds.get(key.toString().concat("Bytemode").getBytes()))   ;
           
            return SerializeUtil.unserialize(jds.hget(id.toString().getBytes(), key.toString().getBytes()));
            // key  -1980593586:486701050:application.dao.CompanyMapper.selectByExample:0:2147483647:
            //SELECT  ID,NAME,CREATE_tIME,UPDATE_tIME,IS_eNABLE,REMARKS,SHORT_nAME,COMPANY_sHORT_nAME,CMS_dOMAIN,PAY_dOMAIN,PC_iP,MOBILE_iP,APP_aPI_aDDRESS,APP_eMBED_aPI_aDDRESS  FROM cOMPANY  WHERE (  IS_eNABLE = ? ) order by SHORT_nAME ASC
            //:true
         //   return     jds.get(key.toString();
            		//jds.get(key.toString());
        } catch (Throwable t) {
            logger.error("Redis get failed, fail over to db", t);
            return null;

