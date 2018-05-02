写一个execTime函数，参数，时间毫秒数，作用：什么都不做，但函数执行会耗时参数传递的毫秒数
ex：


``` js

functime execTime(t) {
  //
}

console.log(1) //输出1
execTime(3000) //运行3秒钟
console.log(2) //3秒后输出2

```

### answer

``` js
function execTime(t) {
  var oldTime = Date.now();
  while(Date.now() < oldTime + t) {

  }
}


```

写一个execTime函数，参数t：时间毫秒数，参数callback：回调函数。
ex：


``` js

functime execTime(t, callback) {
  //
}

console.log(1)
execTime(3000, function() {
  console.log(3)
})
console.log(2)

//执行结果为：立即输出1和2,3秒后输出3

```

### answer

``` js
function execTime(t, callback) {
  setTimeout(t,callback)
}


```