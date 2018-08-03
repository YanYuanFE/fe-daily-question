写一个对象Bus，提供on、emit方法，on实现监听，emit实现触发功能，使用如下方式使用：

Bus.on('event', function(data) {
  console.log(data);
})

Bus.on('hi', function(data) {
  console.log(data);
})

Bus.emit('event', {name: 'hello'});
Bus.emit('hi', {to: 'hunger'});
Bus.emit('hi', {to: 'valley'});


``` js
var Bus = (function() {
  var callbacks = {};
  function on (event, callback) {
    if (!callbacks[event]) {
      callbacks[event] = [callback];
    } else {
      callbacks[event].push(callback);
    }
  }

  function emit (event, data) {
    if (callbacks[event]) {
      callbacks[event].forEach(function(cb) {
        cb(data);
      })
    }
  }
  return {
    on: on,
    emit: emit
  }
})();

```