给定整数n和m，写一个函数dispatch(n, m),把1-n尽量平均地分成m个组。
ex：


``` js

dispatch(6, 3)

// [[1,2], [3,4], [5,6]]

dispatch(9, 2)

// [[1,2,3,4,5], [6,7,8,9]]

```

### answer

``` js

function dispatch(n, m) {
  let maxSize = Math.ceil(n/m);
  let minSize = maxSize -1;
  let minCount = maxSize*m -n;
  let maxCount = m - minCount;
  let arr = [];
  let k =1;
  for (let i=0; i < maxCount; i++) {
    let tempArr = [];
    arr.push(tempArr);
    for(let j = 0; j < maxSize; j++,k++) {
      tempArr.push(k);
    }
  }
  for (let i=0; i < minCount; i++) {
    let tempArr = [];
    arr.push(tempArr);
    for(let j = 0; j < minSize; j++,k++) {
      tempArr.push(k);
    }
  }
  return arr;

}

console.log(dispatch(12, 4));
console.log(dispatch(8, 5));
console.log(dispatch(8, 4));

```
