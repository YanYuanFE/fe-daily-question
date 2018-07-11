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

写一个排序函数sort，满足以下条件：sort接收一个数组（数组里面只会含有正整数，最大数字约为200）
sort将该数组按从小到大的顺序排列，sort返回修改后的数组，
对时间复杂度、空间复杂度均无要求，只要能排序不报错就行。
ex：

### answer

``` js

function sort(arr) {
  return arr.sort((a, b) => a - b);
}

function sort(array) {
  //O(n^2)
  if (array.length >= 2) {
    const round = array.length - 1;
    for (let i=1; i< round; i++) {
      for (let j=0; j < array.length - i; j++) {
        if (array[j] > array[j+1]) {
          let temp = array[j];
          array[j] = array[j+1];
          array[j+1] = temp;
        }
      }
    }
  }
  return array;
}

console.log(sort[1,4,3,4,2,5,])

```

给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。
不要使用额外的数组空间，你必须在原地修改输入数组并在使用O（1）额外空间的条件下完成。

示例：
给定数组nums=[1,1,2,3,2,5],函数应该返回新的长度4,并且原数组nums去除了重复出现的数字。

var removeDuplications = function(nums) {
  //
}

### answer

``` js
var removeDuplicates = function (nums) {
  let dict = {};
  for (let i = nums.length - 1; i >= 0; i--) {
    if (dict[nums[i]]) {
      nums.splice(i, 1)
    } else {
      dict[nums[i]] = true;
    }
  }
  return nums.length;
};

let nums = [2,3,3,4,1,4,6];
removeDuplicates(nums);
console.log(nums);

```