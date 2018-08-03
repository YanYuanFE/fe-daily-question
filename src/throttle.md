实现一个throttle函数,throttle(function, wait, [options]),创建并返回一个像节流阀一样的函数，当重复调用函数的时候，至少每隔 wait毫秒调用一次该函数。对于想控制一些触发频率较高的事件有帮助。
ex：


``` js

// 默认情况下，throttle将在你调用的第一时间尽快执行这个function
// 并且，如果你在wait周期内调用任意次数的函数，都将尽快的被覆盖，
// 如果你响调用第一次首先执行的话，传递{leading: false};
// 还有如果你想调用最后一次执行的话，传递{trailing: false};

var throttled = throttle(updatePosition, 100);
$(window).scroll(throttled);

// 效果是随着scroll事件的触发, 每过100毫秒才执行一次， updatePosition函数

```

### answer

``` js

function now() {
  return new Date().getTime();
}

function throttle(func, wait, options) {
  var context, args, result;
  var timeout = null;
  var previous = 0;
  if (!options) options = {};

  var later = function() {
    previous = options.leading === false ? 0 : now();
    timeout = null;
    result = func.apply(context, args);
    if (!timeout) context = args = null;
  };

  return function() {
    var now = now();
    if (!previous && options.leading === false) previous = now;
    var remaining = wait - (now - previous);
    context = this;
    args = arguments;
    if (remaining <= 0 || remaining > wait) {
      if(timeout) {
        clearTimeout(timeout);
        timeout = null;
      }
      previous = now;
      result = func.apply(context, args);
      if (!timeout) context = args = null;
    } else if (!timeout && options.trailing !== false) {
      timeout = setTimeout(later, remaining);
    }
    return result;
  };
};

```

写一个debounce函数，可以按照如下方式调用，实现的效果是：当连续滚动窗口时，滚动停下300ms后才执行print。

### answer

``` js
function debounce(fn, time) {
  var timer = null;
  return function() {
    clearTimeout(timer);
    timer = setTimeout(fn, time);
  }
}

function print() {
  console.log('print');
}

window.addEventListener('scroll', debounce(print, 300)); 
```

写一个throttle函数，可以按照如下方式调用，实现的效果是：当连续滚动窗口时，莓100ms至多执行一次print。

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

写一个防抖函数

``` js

function debounce(func, delay) {
  var timeout;
  return function (e) {
    var context = this, args = arguments;
    timeout = setTimeout(function() {
      func.apply(context, args);
    }, delay);
  };
};
```

写一个节流函数

``` js

function throttle(fn, threshhold) {
  var timeout;
  var start = new Date;
  var threshhold = threshhold || 160;
  return function (e) {
    var context = this, args = arguments, curr = new Date() - 0;
    clearTimeout(timeout);
    if (curr - start >= threshhold) {
      func.apply(context, args);
      start = curr;
    } else {
      timeout = setTimeout(function() {
        func.apply(context, args);
      }, threshhold);
    } 
  };
};
```