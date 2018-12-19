# array-unique
数组去重

## 来源
- [GitHub](https://github.com/jonschlinkert/array-unique)

## 示例
```js
var unique = require('array-unique');

var arr = ['a', 'b', 'c', 'c'];
console.log(unique(arr)) //=> ['a', 'b', 'c']
console.log(arr)         //=> ['a', 'b', 'c']

/* The above modifies the input array. To prevent that at a slight performance cost: */
var unique = require("array-unique").immutable;

var arr = ['a', 'b', 'c', 'c'];
console.log(unique(arr)) //=> ['a', 'b', 'c']
console.log(arr)         //=> ['a', 'b', 'c', 'c']
```

## 源码
```js
module.exports = function unique(arr) {
  if (!Array.isArray(arr)) {
    throw new TypeError('array-unique expects an array.');
  }

  var len = arr.length;
  var i = -1;

  while (i++ < len) {
    var j = i + 1;

    for (; j < arr.length; ++j) {
      if (arr[i] === arr[j]) {
        arr.splice(j--, 1);
      }
    }
  }
  return arr;
};

module.exports.immutable = function uniqueImmutable(arr) {
  if (!Array.isArray(arr)) {
    throw new TypeError('array-unique expects an array.');
  }

  var arrLen = arr.length;
  var newArr = new Array(arrLen);

  for (var i = 0; i < arrLen; i++) {
    newArr[i] = arr[i];
  }

  // 调用 unique 函数
  return module.exports(newArr);
};
```