写一个byField函数，实现数组按姓名、年纪、任意字段排序
ex：


``` js

var users= [
  { name: 'John', age: 20, company: 'Jirengu'},
  { name: 'Pete', age: 18, company: 'Alibaba'},
  { name: 'Ann', age: 19, company: 'Tencent'},
]

users.sort(byField('company'))

// [
//   { name: 'Pete', age: 18, company: 'Alibaba'},
//   { name: 'John', age: 20, company: 'Jirengu'},
//   { name: 'Ann', age: 19, company: 'Tencent'},
// ]

```

### answer

``` js
const byField = (key) => {
  return (obj1, obj2) => obj1[key] > obj2[key]
}


```