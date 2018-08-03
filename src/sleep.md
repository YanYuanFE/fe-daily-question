写一个函数。

### answer

``` js
function throttle(fn, time) {
  let start = 0;
  return function() {
    let now = +new Date();
    if (now - start >= time) {
      fn();
      start = now;
    }
  }
}

function print() {
  console.log('print');
}

window.addEventListener('scroll', throttle(print, 100)); 
```