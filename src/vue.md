简单模拟Vue的数据代理功能。

function Vue(options) {
  //
}

let app = new Vue({
  data: {
    message: 'Hi'
  }
});

console.log(app.message);

``` js
function Vue(options) {
  let { data } = options;
  this.data = data;
  for(let key in data) {
    Object.defineProperty(this, key, {
      get() {
        return this.data[key];
      },
      set(value) {
        this.data[key] = value;
      }
    })
  }
}

```

简单模拟Vue的computed功能：

``` js
function Vue(options) {
  //
}

let app = new Vue({
  data: {
    firstName: 'Frank',
    lastName: 'Jack',
  },
  computed: {
    name() {
      return this.firstName + ' ' + this.lastName;
    }
  }
});

console.log(app.name); // 'Frank Jack'

app.firstName = 'Tom';

console.log(app.name); // 'Frank Tom'

// 不要求实现app的赋值操作
```

### answer

``` js
function Vue(options) {
  let { data, computed } = options;
  for(let key in data) {
    Object.defineProperty(this, key, {
      get() {
        return data[key];
      },
      set(value) {
        data[key] = value;
      }
    })
  }
  for(let key in computed) {
    Object.defineProperty(this, key, {
      get() {
        return computed[key].call(this);
      }
    })
  }
}
```

登录修改密码退出 1
用户管理 1
渠道管理 1
应用管理 1
检测模块 列表、添加 1
检测项目管理 3
检测结果 3