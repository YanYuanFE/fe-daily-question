创建一个after函数, 只有在运行了 count 次之后才有效果. 在处理同组异步请求返回结果时, 如果你要确保同组里所有异步请求完成之后才 执行这个函数, 这将非常有用。
ex：


``` js

//传参 immediate 为 true， debounce会在wait时间间隔的开始调用这个函数，并且在wait的时间之内，不会再次调用
var renderNotes = after(notes.length, render);
notes.map(function(note) {
  note.asyncSave({success: renderNotes});
})

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
