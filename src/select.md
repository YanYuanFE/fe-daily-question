
ex：


``` js

const obj = {a: 1, b: 2, c: 3};

function select(obj, arr) {
  //
}

select(obj, ["a", "c"])



```

### answer

``` js

function after(times, func) {
  return function() {
    if (--times < 1) {
      return func.apply(this, arguments);
    }
  }
}

```
