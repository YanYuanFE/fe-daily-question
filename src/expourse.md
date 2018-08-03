写一个曝光组件Expourse，实现当dom元素出现在浏览器窗口视野中时，执行回调函数，只执行一次。其中回调函数中的this代表dom元素。

var exposure = new Exposure(node);

exposure.once(function() {
  console.log(this); //this代表node
  console.log('world') //node曝光时执行且只执行一次
})

### Answer

``` js

class Exposure {
  constructor(node) {
    this.node = node;
    this.showed = false;

    window.addEventListener('scroll', this.check.bind(this))
    this.check();
  }

  once(cb) {
    this.callback = cb;
  }

  check() {
    if (this.callback && !this.showed && this.isShow(this.node)) {
      this.showed = true;
      this.callback.bind(this.node)()
    }
  }

  isShow() {
    let el = this.node, top = el.offsetTop, height = el.offsetHeight;
    while (el.offsetParent) {
      el = el.offsetParent;
      top += el.offsetTop;
    }
    return top < window.scrollY + window.innerHeight && top + height > window.scrollY;
  }
}

let exposure = new Exposure(document.querySelector('#node'));

exposure.once(function() {
  console.log('show');
});
```