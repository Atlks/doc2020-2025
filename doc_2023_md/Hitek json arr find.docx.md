Hitek json arr find  lodash




Where 语句实现  filter


rzt=_.filter(db.data, { 'age': 129  }) 


Ordferby  sortBy

_.sortBy(users, function(o) { return o.user; });
// => objects for [['barney', 36], ['barney', 34], ['fred', 48], ['fred', 40]]
 
_.sortBy(users, ['user', 'age']);




Limit     。。数组的截取即可slice

Select  **  map


var users = [
  { 'user': 'barney' },
  { 'user': 'fred' }
];
 
// The `_.property` iteratee shorthand.
_.map(users, 'user');
// => ['barney', 'fred']



