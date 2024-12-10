Golan unsrl json arr

结构体数组
俩种方式，一种直接反序列化成 结构体数组，另一种反序列化为 slice，内容为map[string]interface{}


结构体数组
俩种方式，一种直接反序列化成 结构体数组，另一种反序列化为 slice，内容为map[string]interface{}
 复制
slice
str := `[{"Name":"张三丰","Age":98,"Birthday":"2001-09-21","Sal":3800.85,"Skill":"武当剑法"},{"Name":"张无忌","Age":28,"Birthday":"2004-09-21","Sal":300.85,"Skill":"乾坤大挪移"}]`
​//定义一个slicevar slice []map[string]interface{}//注意：反序列化map,不需要make，因为make操作被封装到Unmarshal函数err := json.Unmarshal([]byte(str), &slice)if err != nil {
fmt.Printf("unmarshal err=%v\n", err)}
fmt.Printf("反序列化后 slice=%v\n", slice)

