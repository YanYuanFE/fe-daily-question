以下代码输出什么？为什么？


ex：

``` js
var app = {
  fn1: function() {
    console.log(this);
  },
  fn2: function() {
    return function() {
      console.log(this);
    }
  },
  fn3: function() {
    function fn() {
      console.log(this)
    }
    fn()
  },
  fn4: function() {
    return {
      fn: function() {
        console.log(this)
      }
    }
  },
  fn5() {
    setTimeout(function() {
      console.log(this)
    }, 10)
  },
  fn6() {
    setTimeout(() => {
      console.log(this);
    }, 20)
  },
  fn7() {
    setTimeout((function() {
      console.log(this)
    }).bind(this), 30)
  },
  fn8: () => {
    setTimeout(() => {
      console.log(this);
    }, 40)
  }
}

app.fn1();
app.fn2()();
app.fn3();
app.fn4().fn();
app.fn5();
app.fn6();
app.fn7();
app.fn8();
```

### answer:

``` js
app;
window;
window;
fn4;
window;
app;
app;
window;

```
以下代码输出什么？为什么？

``` js
var a = 1;
function fn1() {
  function fn3() {
    function fn2() {
      console.log(a);
    }
    var a;
    fn2();
    a = 4;
  }
  var a = 2;
  return fn3;
}

var fn = fn1();
fn() //
```

### answer

输出undefined

变量提升后

``` js
var a = 1;
var fn;
function fn1() {
  function fn3() {
    var a;
    function fn2() {
      console.log(a);
    }
    fn2();
    a = 4;
  }
  a = 2;
  return fn3;
}

fn = fn1();
fn()

```