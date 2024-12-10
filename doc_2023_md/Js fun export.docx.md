Js fun export  



解构赋值
使用数组成员对变量赋值时，优先使用解构赋值。
const arr = [1, 2, 3, 4];
// badconst first = arr[0];const second = arr[1];
// goodconst [first, second] = arr;
函数的参数如果是对象的成员，优先使用解构赋值。
// badfunction getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;}



// goodfunction getFullName(obj) {
  const { firstName, lastName } = obj;}
// bestfunction getFullName({ firstName, lastName }) {}

