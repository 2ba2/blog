# arr-union
取多个数组的元素去重后组成一个数组

## 来源
- [GitHub](https://github.com/jonschlinkert/arr-union)

## 示例
```js
var union = require('arr-union');

union(['a'], ['b', 'c'], ['d', 'e', 'f']);
//=> ['a', 'b', 'c', 'd', 'e', 'f']

union(['a', 'a'], ['b', 'c']);
//=> ['a', 'b', 'c']
```

## 源码
```js
module.exports = function union(init) {
  if (!Array.isArray(init)) {
    throw new TypeError('arr-union expects the first argument to be an array.');
  }

  var len = arguments.length;
  var i = 0;

  while (++i < len) {
    var arg = arguments[i];
    // 忽略假值
    if (!arg) continue;

    // 把非数组元素包装成数组
    if (!Array.isArray(arg)) {
      arg = [arg];
    }

    for (var j = 0; j < arg.length; j++) {
      var ele = arg[j];
      // 判断是否重复
      if (init.indexOf(ele) >= 0) {
        continue;
      }
      init.push(ele);
    }
  }
  return init;
};
```
