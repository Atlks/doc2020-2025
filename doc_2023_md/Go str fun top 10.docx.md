Go str fun top 10




Ref mysql str fun


package libcn

import (
    "goapiPrj/lib"
    "strings"
)

func F长度(字符串 string) int {
    return lib.Len(字符串)
}

func 长度(字符串 string) int {
    return lib.Len(字符串)
}

func F修剪空格(字符串 string) string {
    return strings.TrimSpace(字符串)

}

func F截取(字符串 string, 开始位置 int, 结束位置 int) string {
    return lib.Substr(字符串, 开始位置, 结束位置)

}

func F左截取(字符串 string, 长度 int) string {
    return lib.Left(字符串, 长度)
}

func F右截取(字符串 string, 长度 int) string {
    return lib.Right(字符串, 长度)
}

func F替换(字符串 string, 旧子串 string, 新子串 string) string {

    // v (s, old, new string, n int)
    return strings.Replace(字符串, 旧子串, 新子串, -1)
}

func F连接(字符串1 string, 字符串2 string) string {

    return 字符串1 + 字符串2
}
func F拆分(字符串 string, 拆分子串 string) []string {
    return strings.Split(字符串, 拆分子串)

}

