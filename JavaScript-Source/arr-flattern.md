# arr-flatten
将多维数组展平为一维数组

## 来源
- [GitHub](https://github.com/jonschlinkert/arr-flatten)

## 示例
```js
var flatten = require('arr-flatten');

flatten(['a', ['b', ['c']], 'd', ['e']]);
//=> ['a', 'b', 'c', 'd', 'e']
```

## 源码
```js
module.exports = function (arr) {
  return flat(arr, []);
};

// 递归展平数组
function flat(arr, res) {
  var i = 0, cur;
  var len = arr.length;
  for (; i < len; i++) {
    cur = arr[i];
    Array.isArray(cur) ? flat(cur, res) : res.push(cur);
  }
  return res;
}
```
