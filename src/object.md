用js写出一个对象obj，使得obj.obj.obj.obj.obj === obj，也就是说，不管出现多少次.obj，都得到obj。

### answer

``` js
var obj = {};
obj.obj = obj;


```

