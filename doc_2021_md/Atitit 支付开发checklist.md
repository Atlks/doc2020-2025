Atitit 支付开发checklist


签名规则
采用MD5 加密方式对传输数据进行签名验证，具体请参考相关接口定义。对MD5 加密后的签名值，请注意结果的大小写务必正确。
筛选
根据相关接口定义当签名为√的参数均需参与签名。sign参数除外。
排序
将筛选的参数按照第一个字符的键值ASCII码递增排序（字母升序排序），如果遇到相同字符则按照第二个字符的键值ASCII码递增排序，以此类推。
拼接
将排序后的参数与其对应值，组合成“参数=参数值”的格式，并且把这些参数用&字符连接起来，此时生成的字符串为待签名字符串。MD5签名的商户需要将key的值拼接在字符串后面，调用MD5算法生成sign。
商户如用提供的demo集成，demo已写好签名验签的方法，商户可直接调用，如自己开发不用demo，则按以上方法拼接待签名字符串。 

大小写

可以使用俩种延签模式策略模式
单元测试
springtest

