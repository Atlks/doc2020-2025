Atitit map抓换xml




  public static void main(String[] args) {

        // 1. 定义一个map
        Map<String,String> map = new HashMap<String,String>();
        map.put("name","chris");
        map.put("island","faranga");

        // 2. 生成xml根标签
        XStream xStream = new XStream();
     //   xStream.registerConverter(new MapEntryConverter());
   //     xStream.alias("root", Map.class);

        // 3. 将map转换成xml格式
        String xml = xStream.toXML(map);
        System.out.println(xml);

        // 4. 解析xml字符串并转换为Map
        Map  extractedMap = (Map ) xStream.fromXML(xml);
        System.out.println(extractedMap);


<map>
  <entry>
    <string>island</string>
    <string>faranga</string>
  </entry>
  <entry>
    <string>name</string>
    <string>chris</string>
  </entry>
</map>



{island=faranga, name=chris}
