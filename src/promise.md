小明成绩不好，每次考试都靠瞎猜。小明的老师对他说:小明，如果考不到60分你继续考，直到考到60分，我实现你的愿望让你和凯丽坐到一起。

ex：


``` js

function exam() {
  var score = Math.floor(Math.random() * 101);
  if (score >= 60) {
    console.log('及格，和凯丽坐到一起');
  } else {
    console.log('不及格，继续考试');
    setTimeout(exam, 1000)
  }
}

exam();

```
对上述代码用Promise改写，能用以下方式调用：
``` js

exam().then(score => {
  console.log('及格，和凯丽坐到一起', score)
})

```

### answer

``` js
const axam = () => {
  return new Promise((resolve, reject) => {
    const score = Math.floor(Math.random() * 101);
    if (score >= 60) {
      resolve(score);
    } else {
      console.log('不及格，继续考试');
      setTimeout(() => resolve(exam()), 1000);
    }
  })
}

```
