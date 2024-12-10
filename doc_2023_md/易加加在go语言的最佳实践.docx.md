易加加在go语言的最佳实践



公共函数必须F因为开头，不然中文识别为私有函数

模块文件夹不能为中文
易语言测试.go:6:2: malformed import path "goapiPrj/类库": invalid char '类'

包名可以为中文

package 类库包

import (
    "goapiPrj/lib"
    "strings"
)

func F长度(字符串 string) int {
    return lib.Len(字符串)
}



类库别名可以为中文

import (
    "goapiPrj/lib"
    类库包 "goapiPrj/libcn"
)

