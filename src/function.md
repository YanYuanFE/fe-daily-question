写出一个函数fn,使得fn满足以下条件：
1、fn() === fn
2、fn.fn === fn

### answer

``` js
function fn() {
  return fn;
}

fn.fn = fn;


```

写出一个函数fn，使得fn满足以下条件：
1、fn()打印出'a'
1、fn()()打印出'b'
1、fn()()()打印出'c'

### answer

``` js
const fn =() => {
  let str = 'a';
  console.log(str);
  return () => {
    str = 'b';
    return () => {
      str = 'c'
    }
  }
}


```

写出一个函数fn，使得fn满足以下条件：
1、fn() == 'a'
1、fn()() == 'b'
1、fn()()() == 'c'

### answer

``` js
const fn =() => {
  const a = () => b;
  const b = () => 'c';
  a.valueOf = () => 'a';
  b.valueOf = () => 'b';
  return a;
}


function fn() {
  function fn2() {
    function fn3() {
      function fn4() {
      }
      fn4.toString = () => 'c';
      return fn4();
    }
    fn3.toString = () => 'b';
    return fn3();
  }
  fn2.toString = () => 'b';
  return fn2();
}


```