# arr-diff
比较数组，得到数组不同的部分。

## 来源
- [GitHub](https://github.com/jonschlinkert/arr-diff)

## 示例
```js
var diff = require('arr-diff');

var a = ['a', 'b', 'c', 'd'];
var b = ['b', 'c'];

console.log(diff(a, b))
//=> ['a', 'd']
```

## 源码
```js
module.exports = function diff(arr/*, arrays*/) {
  var len = arguments.length;
  var idx = 0;
  
  // 多次调用 比较方法比较多个数组
  while (++idx < len) {
    arr = diffArray(arr, arguments[idx]);
  }
  return arr;
};

function diffArray(one, two) {
  if (!Array.isArray(two)) {
    return one.slice();
  }

  var tlen = two.length
  var olen = one.length;
  var idx = -1;
  var arr = [];

  // 取 one 中的元素和 two 中的元素对比
  while (++idx < olen) {
    var ele = one[idx];

    var hasEle = false;
    for (var i = 0; i < tlen; i++) {
      var val = two[i];

      if (ele === val) {
        hasEle = true;
        break;
      }
    }

    if (hasEle === false) {
      arr.push(ele);
    }
  }
  return arr;
}
```
