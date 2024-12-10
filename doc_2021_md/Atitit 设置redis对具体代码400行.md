Atitit 设置redis对具体代码400行

	 Jedis jedis = new Jedis("localhost");
		  jedis.set("LHC_NEED_11086", "1");
		  System.out.println("f");

使用javaagent跟踪每个方法

>>>> call: util.ShellUtil__main([Ljava.lang.String;@21bcffb5) 
>>>> call: redis.clients.jedis.Jedis__Jedis(localhost) 
>>>> call: redis.clients.jedis.BinaryJedis__BinaryJedis(localhost) 
>>>> call: redis.clients.jedis.Client__Client(localhost) 
>>>> call: redis.clients.jedis.BinaryClient__BinaryClient(localhost) 
>>>> call: redis.clients.jedis.Connection__Connection(localhost) 
	<<redis.clients.jedis.Connection__Connection() ret:null
	<<redis.clients.jedis.BinaryClient__BinaryClient() ret:null
	<<redis.clients.jedis.Client__Client() ret:null
	<<redis.clients.jedis.BinaryJedis__BinaryJedis() ret:null
	<<redis.clients.jedis.Jedis__Jedis() ret:null
>>>> call: redis.clients.jedis.Jedis__set(LHC_NEED_11086, 1) 
>>>> call: redis.clients.jedis.BinaryJedis__checkIsInMulti() 
>>>> call: redis.clients.jedis.BinaryClient__isInMulti() 
	<<redis.clients.jedis.BinaryClient__isInMulti() ret:false
	<<redis.clients.jedis.BinaryJedis__checkIsInMulti() ret:null
>>>> call: redis.clients.jedis.Client__set(LHC_NEED_11086, 1) 
>>>> call: redis.clients.util.SafeEncoder__encode(LHC_NEED_11086) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@457e2f02
>>>> call: redis.clients.util.SafeEncoder__encode(1) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5c7fa833
>>>> call: redis.clients.jedis.BinaryClient__set([B@457e2f02, [B@5c7fa833) 
>>>> call: redis.clients.util.SafeEncoder__encode(PING) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@39aeed2f
>>>> call: redis.clients.util.SafeEncoder__encode(SET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@724af044
>>>> call: redis.clients.util.SafeEncoder__encode(GET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4678c730
>>>> call: redis.clients.util.SafeEncoder__encode(QUIT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6767c1fc
>>>> call: redis.clients.util.SafeEncoder__encode(EXISTS) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@29ee9faa
>>>> call: redis.clients.util.SafeEncoder__encode(DEL) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@c038203
>>>> call: redis.clients.util.SafeEncoder__encode(TYPE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@cc285f4
>>>> call: redis.clients.util.SafeEncoder__encode(FLUSHDB) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@55f3ddb1
>>>> call: redis.clients.util.SafeEncoder__encode(KEYS) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@8bd1b6a
>>>> call: redis.clients.util.SafeEncoder__encode(RANDOMKEY) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@18be83e4
>>>> call: redis.clients.util.SafeEncoder__encode(RENAME) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@cb5822
>>>> call: redis.clients.util.SafeEncoder__encode(RENAMENX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4b9e13df
>>>> call: redis.clients.util.SafeEncoder__encode(RENAMEX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@2b98378d
>>>> call: redis.clients.util.SafeEncoder__encode(DBSIZE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@475530b9
>>>> call: redis.clients.util.SafeEncoder__encode(EXPIRE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1d057a39
>>>> call: redis.clients.util.SafeEncoder__encode(EXPIREAT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@26be92ad
>>>> call: redis.clients.util.SafeEncoder__encode(TTL) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4c70fda8
>>>> call: redis.clients.util.SafeEncoder__encode(SELECT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@224edc67
>>>> call: redis.clients.util.SafeEncoder__encode(MOVE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@14acaea5
>>>> call: redis.clients.util.SafeEncoder__encode(FLUSHALL) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@46d56d67
>>>> call: redis.clients.util.SafeEncoder__encode(GETSET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@d8355a8
>>>> call: redis.clients.util.SafeEncoder__encode(MGET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@59fa1d9b
>>>> call: redis.clients.util.SafeEncoder__encode(SETNX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@28d25987
>>>> call: redis.clients.util.SafeEncoder__encode(SETEX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4501b7af
>>>> call: redis.clients.util.SafeEncoder__encode(MSET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@523884b2
>>>> call: redis.clients.util.SafeEncoder__encode(MSETNX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5b275dab
>>>> call: redis.clients.util.SafeEncoder__encode(DECRBY) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@61832929
>>>> call: redis.clients.util.SafeEncoder__encode(DECR) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@29774679
>>>> call: redis.clients.util.SafeEncoder__encode(INCRBY) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3ffc5af1
>>>> call: redis.clients.util.SafeEncoder__encode(INCR) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5e5792a0
>>>> call: redis.clients.util.SafeEncoder__encode(APPEND) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@26653222
>>>> call: redis.clients.util.SafeEncoder__encode(SUBSTR) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3532ec19
>>>> call: redis.clients.util.SafeEncoder__encode(HSET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@68c4039c
>>>> call: redis.clients.util.SafeEncoder__encode(HGET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@ae45eb6
>>>> call: redis.clients.util.SafeEncoder__encode(HSETNX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@59f99ea
>>>> call: redis.clients.util.SafeEncoder__encode(HMSET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@27efef64
>>>> call: redis.clients.util.SafeEncoder__encode(HMGET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6f7fd0e6
>>>> call: redis.clients.util.SafeEncoder__encode(HINCRBY) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@47c62251
>>>> call: redis.clients.util.SafeEncoder__encode(HEXISTS) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3e6fa38a
>>>> call: redis.clients.util.SafeEncoder__encode(HDEL) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@66a3ffec
>>>> call: redis.clients.util.SafeEncoder__encode(HLEN) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@77caeb3e
>>>> call: redis.clients.util.SafeEncoder__encode(HKEYS) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1e88b3c
>>>> call: redis.clients.util.SafeEncoder__encode(HVALS) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@42d80b78
>>>> call: redis.clients.util.SafeEncoder__encode(HGETALL) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3bfdc050
>>>> call: redis.clients.util.SafeEncoder__encode(RPUSH) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1bce4f0a
>>>> call: redis.clients.util.SafeEncoder__encode(LPUSH) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5e3a8624
>>>> call: redis.clients.util.SafeEncoder__encode(LLEN) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5c3bd550
>>>> call: redis.clients.util.SafeEncoder__encode(LRANGE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@91161c7
>>>> call: redis.clients.util.SafeEncoder__encode(LTRIM) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@604ed9f0
>>>> call: redis.clients.util.SafeEncoder__encode(LINDEX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6a4f787b
>>>> call: redis.clients.util.SafeEncoder__encode(LSET) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@685cb137
>>>> call: redis.clients.util.SafeEncoder__encode(LREM) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6a41eaa2
>>>> call: redis.clients.util.SafeEncoder__encode(LPOP) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@7cd62f43
>>>> call: redis.clients.util.SafeEncoder__encode(RPOP) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6d4b1c02
>>>> call: redis.clients.util.SafeEncoder__encode(RPOPLPUSH) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6093dd95
>>>> call: redis.clients.util.SafeEncoder__encode(SADD) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5622fdf
>>>> call: redis.clients.util.SafeEncoder__encode(SMEMBERS) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4883b407
>>>> call: redis.clients.util.SafeEncoder__encode(SREM) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@7d9d1a19
>>>> call: redis.clients.util.SafeEncoder__encode(SPOP) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@39c0f4a
>>>> call: redis.clients.util.SafeEncoder__encode(SMOVE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1794d431
>>>> call: redis.clients.util.SafeEncoder__encode(SCARD) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@42e26948
>>>> call: redis.clients.util.SafeEncoder__encode(SISMEMBER) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@57baeedf
>>>> call: redis.clients.util.SafeEncoder__encode(SINTER) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@343f4d3d
>>>> call: redis.clients.util.SafeEncoder__encode(SINTERSTORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@53b32d7
>>>> call: redis.clients.util.SafeEncoder__encode(SUNION) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5442a311
>>>> call: redis.clients.util.SafeEncoder__encode(SUNIONSTORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@548e7350
>>>> call: redis.clients.util.SafeEncoder__encode(SDIFF) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1a968a59
>>>> call: redis.clients.util.SafeEncoder__encode(SDIFFSTORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4667ae56
>>>> call: redis.clients.util.SafeEncoder__encode(SRANDMEMBER) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@77cd7a0
>>>> call: redis.clients.util.SafeEncoder__encode(ZADD) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@204f30ec
>>>> call: redis.clients.util.SafeEncoder__encode(ZRANGE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@e25b2fe
>>>> call: redis.clients.util.SafeEncoder__encode(ZREM) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@754ba872
>>>> call: redis.clients.util.SafeEncoder__encode(ZINCRBY) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@146ba0ac
>>>> call: redis.clients.util.SafeEncoder__encode(ZRANK) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4dfa3a9d
>>>> call: redis.clients.util.SafeEncoder__encode(ZREVRANK) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6eebc39e
>>>> call: redis.clients.util.SafeEncoder__encode(ZREVRANGE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@464bee09
>>>> call: redis.clients.util.SafeEncoder__encode(ZCARD) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@f6c48ac
>>>> call: redis.clients.util.SafeEncoder__encode(ZSCORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@13deb50e
>>>> call: redis.clients.util.SafeEncoder__encode(MULTI) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@239963d8
>>>> call: redis.clients.util.SafeEncoder__encode(DISCARD) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3abbfa04
>>>> call: redis.clients.util.SafeEncoder__encode(EXEC) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@57fffcd7
>>>> call: redis.clients.util.SafeEncoder__encode(WATCH) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@31ef45e3
>>>> call: redis.clients.util.SafeEncoder__encode(UNWATCH) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@598067a5
>>>> call: redis.clients.util.SafeEncoder__encode(SORT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3c0ecd4b
>>>> call: redis.clients.util.SafeEncoder__encode(BLPOP) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@14bf9759
>>>> call: redis.clients.util.SafeEncoder__encode(BRPOP) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5f341870
>>>> call: redis.clients.util.SafeEncoder__encode(AUTH) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@553f17c
>>>> call: redis.clients.util.SafeEncoder__encode(SUBSCRIBE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4f7d0008
>>>> call: redis.clients.util.SafeEncoder__encode(PUBLISH) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@271053e1
>>>> call: redis.clients.util.SafeEncoder__encode(UNSUBSCRIBE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@589838eb
>>>> call: redis.clients.util.SafeEncoder__encode(PSUBSCRIBE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@42dafa95
>>>> call: redis.clients.util.SafeEncoder__encode(PUNSUBSCRIBE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6500df86
>>>> call: redis.clients.util.SafeEncoder__encode(PUBSUB) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@402a079c
>>>> call: redis.clients.util.SafeEncoder__encode(ZCOUNT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@59ec2012
>>>> call: redis.clients.util.SafeEncoder__encode(ZRANGEBYSCORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4cf777e8
>>>> call: redis.clients.util.SafeEncoder__encode(ZREVRANGEBYSCORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@2f686d1f
>>>> call: redis.clients.util.SafeEncoder__encode(ZREMRANGEBYRANK) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3fee9989
>>>> call: redis.clients.util.SafeEncoder__encode(ZREMRANGEBYSCORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@73ad2d6
>>>> call: redis.clients.util.SafeEncoder__encode(ZUNIONSTORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@7085bdee
>>>> call: redis.clients.util.SafeEncoder__encode(ZINTERSTORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1ce92674
>>>> call: redis.clients.util.SafeEncoder__encode(ZLEXCOUNT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5700d6b1
>>>> call: redis.clients.util.SafeEncoder__encode(ZRANGEBYLEX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6fd02e5
>>>> call: redis.clients.util.SafeEncoder__encode(ZREMRANGEBYLEX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5bcab519
>>>> call: redis.clients.util.SafeEncoder__encode(SAVE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@e45f292
>>>> call: redis.clients.util.SafeEncoder__encode(BGSAVE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5f2108b5
>>>> call: redis.clients.util.SafeEncoder__encode(BGREWRITEAOF) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@31a5c39e
>>>> call: redis.clients.util.SafeEncoder__encode(LASTSAVE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3f49dace
>>>> call: redis.clients.util.SafeEncoder__encode(SHUTDOWN) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1e397ed7
>>>> call: redis.clients.util.SafeEncoder__encode(INFO) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@490ab905
>>>> call: redis.clients.util.SafeEncoder__encode(MONITOR) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@56ac3a89
>>>> call: redis.clients.util.SafeEncoder__encode(SLAVEOF) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@27c20538
>>>> call: redis.clients.util.SafeEncoder__encode(CONFIG) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@72d818d1
>>>> call: redis.clients.util.SafeEncoder__encode(STRLEN) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6e06451e
>>>> call: redis.clients.util.SafeEncoder__encode(SYNC) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@59494225
>>>> call: redis.clients.util.SafeEncoder__encode(LPUSHX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6e1567f1
>>>> call: redis.clients.util.SafeEncoder__encode(PERSIST) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5cb9f472
>>>> call: redis.clients.util.SafeEncoder__encode(RPUSHX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@cb644e
>>>> call: redis.clients.util.SafeEncoder__encode(ECHO) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@13805618
>>>> call: redis.clients.util.SafeEncoder__encode(LINSERT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@56ef9176
>>>> call: redis.clients.util.SafeEncoder__encode(DEBUG) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4566e5bd
>>>> call: redis.clients.util.SafeEncoder__encode(BRPOPLPUSH) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1ed4004b
>>>> call: redis.clients.util.SafeEncoder__encode(SETBIT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@ff5b51f
>>>> call: redis.clients.util.SafeEncoder__encode(GETBIT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@25bbe1b6
>>>> call: redis.clients.util.SafeEncoder__encode(BITPOS) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5702b3b1
>>>> call: redis.clients.util.SafeEncoder__encode(SETRANGE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@69ea3742
>>>> call: redis.clients.util.SafeEncoder__encode(GETRANGE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4b952a2d
>>>> call: redis.clients.util.SafeEncoder__encode(EVAL) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3159c4b8
>>>> call: redis.clients.util.SafeEncoder__encode(EVALSHA) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@73846619
>>>> call: redis.clients.util.SafeEncoder__encode(SCRIPT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@4bec1f0c
>>>> call: redis.clients.util.SafeEncoder__encode(SLOWLOG) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@29ca901e
>>>> call: redis.clients.util.SafeEncoder__encode(OBJECT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5649fd9b
>>>> call: redis.clients.util.SafeEncoder__encode(BITCOUNT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6adede5
>>>> call: redis.clients.util.SafeEncoder__encode(BITOP) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@2d928643
>>>> call: redis.clients.util.SafeEncoder__encode(SENTINEL) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@5025a98f
>>>> call: redis.clients.util.SafeEncoder__encode(DUMP) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@49993335
>>>> call: redis.clients.util.SafeEncoder__encode(RESTORE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@20322d26
>>>> call: redis.clients.util.SafeEncoder__encode(PEXPIRE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@192b07fd
>>>> call: redis.clients.util.SafeEncoder__encode(PEXPIREAT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@64bfbc86
>>>> call: redis.clients.util.SafeEncoder__encode(PTTL) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@64bf3bbf
>>>> call: redis.clients.util.SafeEncoder__encode(INCRBYFLOAT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@55d56113
>>>> call: redis.clients.util.SafeEncoder__encode(PSETEX) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@148080bb
>>>> call: redis.clients.util.SafeEncoder__encode(CLIENT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@dc24521
>>>> call: redis.clients.util.SafeEncoder__encode(TIME) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@10bdf5e5
>>>> call: redis.clients.util.SafeEncoder__encode(MIGRATE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@6e1ec318
>>>> call: redis.clients.util.SafeEncoder__encode(HINCRBYFLOAT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@7e0b0338
>>>> call: redis.clients.util.SafeEncoder__encode(SCAN) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@617faa95
>>>> call: redis.clients.util.SafeEncoder__encode(HSCAN) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@1e127982
>>>> call: redis.clients.util.SafeEncoder__encode(SSCAN) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@60c6f5b
>>>> call: redis.clients.util.SafeEncoder__encode(ZSCAN) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@2038ae61
>>>> call: redis.clients.util.SafeEncoder__encode(WAIT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@3c0f93f1
>>>> call: redis.clients.util.SafeEncoder__encode(CLUSTER) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@31dc339b
>>>> call: redis.clients.util.SafeEncoder__encode(ASKING) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@544fe44c
>>>> call: redis.clients.util.SafeEncoder__encode(PFADD) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@31610302
>>>> call: redis.clients.util.SafeEncoder__encode(PFCOUNT) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@71318ec4
>>>> call: redis.clients.util.SafeEncoder__encode(PFMERGE) 
	<<redis.clients.util.SafeEncoder__encode() ret:[B@21213b92
>>>> call: redis.clients.jedis.Connection__sendCommand(SET, [[B@a67c67e) 
>>>> call: redis.clients.jedis.BinaryClient__connect() 
>>>> call: redis.clients.jedis.Connection__isConnected() 
	<<redis.clients.jedis.Connection__isConnected() ret:false
>>>> call: redis.clients.jedis.Connection__connect() 
>>>> call: redis.clients.jedis.Connection__isConnected() 
	<<redis.clients.jedis.Connection__isConnected() ret:false
>>>> call: redis.clients.util.RedisOutputStream__RedisOutputStream(java.net.SocketOutputStream@5383967b) 
>>>> call: redis.clients.util.RedisOutputStream__RedisOutputStream(java.net.SocketOutputStream@5383967b, 8192) 
	<<redis.clients.util.RedisOutputStream__RedisOutputStream() ret:null
	<<redis.clients.util.RedisOutputStream__RedisOutputStream() ret:null
>>>> call: redis.clients.util.RedisInputStream__RedisInputStream(java.net.SocketInputStream@5abca1e0) 
>>>> call: redis.clients.util.RedisInputStream__RedisInputStream(java.net.SocketInputStream@5abca1e0, 8192) 
	<<redis.clients.util.RedisInputStream__RedisInputStream() ret:null
	<<redis.clients.util.RedisInputStream__RedisInputStream() ret:null
	<<redis.clients.jedis.Connection__connect() ret:null
	<<redis.clients.jedis.BinaryClient__connect() ret:null
>>>> call: redis.clients.jedis.Protocol__sendCommand(redis.clients.util.RedisOutputStream@67784306, SET, [[B@a67c67e) 
>>>> call: redis.clients.jedis.Protocol__sendCommand(redis.clients.util.RedisOutputStream@67784306, [B@724af044, [[B@a67c67e) 
>>>> call: redis.clients.util.RedisOutputStream__write(42) 
	<<redis.clients.util.RedisOutputStream__write() ret:null
>>>> call: redis.clients.util.RedisOutputStream__writeIntCrLf(3) 
>>>> call: redis.clients.util.RedisOutputStream__writeCrLf() 
	<<redis.clients.util.RedisOutputStream__writeCrLf() ret:null
	<<redis.clients.util.RedisOutputStream__writeIntCrLf() ret:null
>>>> call: redis.clients.util.RedisOutputStream__write(36) 
	<<redis.clients.util.RedisOutputStream__write() ret:null
>>>> call: redis.clients.util.RedisOutputStream__writeIntCrLf(3) 
>>>> call: redis.clients.util.RedisOutputStream__writeCrLf() 
	<<redis.clients.util.RedisOutputStream__writeCrLf() ret:null
	<<redis.clients.util.RedisOutputStream__writeIntCrLf() ret:null
>>>> call: redis.clients.util.RedisOutputStream__write([B@724af044) 
>>>> call: redis.clients.util.RedisOutputStream__write([B@724af044, 0, 3) 
	<<redis.clients.util.RedisOutputStream__write() ret:null
	<<redis.clients.util.RedisOutputStream__write() ret:null
>>>> call: redis.clients.util.RedisOutputStream__writeCrLf() 
	<<redis.clients.util.RedisOutputStream__writeCrLf() ret:null
>>>> call: redis.clients.util.RedisOutputStream__write(36) 
	<<redis.clients.util.RedisOutputStream__write() ret:null
>>>> call: redis.clients.util.RedisOutputStream__writeIntCrLf(14) 
>>>> call: redis.clients.util.RedisOutputStream__writeCrLf() 
	<<redis.clients.util.RedisOutputStream__writeCrLf() ret:null
	<<redis.clients.util.RedisOutputStream__writeIntCrLf() ret:null
>>>> call: redis.clients.util.RedisOutputStream__write([B@457e2f02) 
>>>> call: redis.clients.util.RedisOutputStream__write([B@457e2f02, 0, 14) 
	<<redis.clients.util.RedisOutputStream__write() ret:null
	<<redis.clients.util.RedisOutputStream__write() ret:null
>>>> call: redis.clients.util.RedisOutputStream__writeCrLf() 
	<<redis.clients.util.RedisOutputStream__writeCrLf() ret:null
>>>> call: redis.clients.util.RedisOutputStream__write(36) 
	<<redis.clients.util.RedisOutputStream__write() ret:null
>>>> call: redis.clients.util.RedisOutputStream__writeIntCrLf(1) 
>>>> call: redis.clients.util.RedisOutputStream__writeCrLf() 
	<<redis.clients.util.RedisOutputStream__writeCrLf() ret:null
	<<redis.clients.util.RedisOutputStream__writeIntCrLf() ret:null
>>>> call: redis.clients.util.RedisOutputStream__write([B@5c7fa833) 
>>>> call: redis.clients.util.RedisOutputStream__write([B@5c7fa833, 0, 1) 
	<<redis.clients.util.RedisOutputStream__write() ret:null
	<<redis.clients.util.RedisOutputStream__write() ret:null
>>>> call: redis.clients.util.RedisOutputStream__writeCrLf() 
	<<redis.clients.util.RedisOutputStream__writeCrLf() ret:null
	<<redis.clients.jedis.Protocol__sendCommand() ret:null
	<<redis.clients.jedis.Protocol__sendCommand() ret:null
	<<redis.clients.jedis.Connection__sendCommand() ret:redis.clients.jedis.Client@335eadca
	<<redis.clients.jedis.BinaryClient__set() ret:null
	<<redis.clients.jedis.Client__set() ret:null
>>>> call: redis.clients.jedis.Connection__getStatusCodeReply() 
>>>> call: redis.clients.jedis.Connection__flush() 
>>>> call: redis.clients.util.RedisOutputStream__flush() 
>>>> call: redis.clients.util.RedisOutputStream__flushBuffer() 
	<<redis.clients.util.RedisOutputStream__flushBuffer() ret:null
	<<redis.clients.util.RedisOutputStream__flush() ret:null
	<<redis.clients.jedis.Connection__flush() ret:null
>>>> call: redis.clients.jedis.Connection__readProtocolWithCheckingBroken() 
>>>> call: redis.clients.jedis.Protocol__read(redis.clients.util.RedisInputStream@210366b4) 
>>>> call: redis.clients.jedis.Protocol__process(redis.clients.util.RedisInputStream@210366b4) 
>>>> call: redis.clients.util.RedisInputStream__readByte() 
>>>> call: redis.clients.util.RedisInputStream__ensureFill() 
	<<redis.clients.util.RedisInputStream__ensureFill() ret:null
	<<redis.clients.util.RedisInputStream__readByte() ret:43
>>>> call: redis.clients.jedis.Protocol__processStatusCodeReply(redis.clients.util.RedisInputStream@210366b4) 
>>>> call: redis.clients.util.RedisInputStream__readLineBytes() 
>>>> call: redis.clients.util.RedisInputStream__ensureFill() 
	<<redis.clients.util.RedisInputStream__ensureFill() ret:null
	<<redis.clients.util.RedisInputStream__readLineBytes() ret:[B@eec5a4a
	<<redis.clients.jedis.Protocol__processStatusCodeReply() ret:[B@eec5a4a
	<<redis.clients.jedis.Protocol__process() ret:[B@eec5a4a
	<<redis.clients.jedis.Protocol__read() ret:[B@eec5a4a
	<<redis.clients.jedis.Connection__readProtocolWithCheckingBroken() ret:[B@eec5a4a
>>>> call: redis.clients.util.SafeEncoder__encode([B@eec5a4a) 
	<<redis.clients.util.SafeEncoder__encode() ret:OK
	<<redis.clients.jedis.Connection__getStatusCodeReply() ret:OK
	<<redis.clients.jedis.Jedis__set() ret:OK
f
	<<util.ShellUtil__main() ret:null

