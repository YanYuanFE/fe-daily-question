``` js

function f() {
  return f;
}
new f() instanceof f;
//  写出执行结果  // false

```

当代码 new f()执行时，下面事情将会发生：

一个新对象被创建。它继承自 f.prototype

构造函数 f被执行。执行的时候，相应的传参会被传入，同时上下文(this)会被指定为这个新实例。 new f等同于 new f()，只能用在不传递任何参数的情况。

如果构造函数返回了一个“对象”，那么这个对象会取代整个 new出来的结果。如果构造函数没有返回对象，那么 new出来的结果为步骤1创建的对象，

ps：一般情况下构造函数不返回任何值，不过用户如果想覆盖这个返回值，可以自己选择返回一个普通对象来覆盖。当然，返回数组也会覆盖，因为数组也是对象

于是，我们这里的 new f()返回的仍然是函数 f本身，而并非他的实例


``` js

Object.prototype.a = 'a';
Function.prototype.a = 'a1';
function Person() {};
var person = new Person();
console.log(person.a); // a

```
![eslint](http://o9qn9041y.bkt.clouddn.com/640.webp)

``` js

var person = {
  n: 1
};

person.x = person = {
  n: 2
};

console.log(person.x);  // undefined

```

person.x = person = { n: 2 }; 这里非常特殊

“.“运算符的优先级要高于”=“的优先级，所以这里的次序是：

1.创建了一个x属性，值为undefined，挂在person下。

2.person的指向被改变，指向了{n:2}。

3.刚才创建的x属性被赋值为{n:2}

4.由于person的指向已经改变，不再指向原有的对象，所以person.x就为undefined。

``` js
<script>
person;
console.log(1);
</script>

<script>
console.log(2);
</script>

```

报错 2

对于 Javascript 而言，我们面对的仅仅只是异常，异常的出现不会直接导致 JS 引擎崩溃，最多只会使当前执行的任务终止。

所以上述过程如下：

1.当前代码块将作为一个任务压入任务队列中，JS 线程会不断地从任务队列中提取任务执行。

2.当任务执行过程中出现异常，且异常没有捕获处理，则会一直沿着调用栈一层层向外抛出，最终终止当前任务的执行。

3.JS 线程会继续从任务队列中提取下一个任务继续执行。

``` js
while(1) {
  switch('person') {
    case 'person':
    // 禁止直接写一句break;
  }
}

// 请修改代码能够跳出死循环
```

