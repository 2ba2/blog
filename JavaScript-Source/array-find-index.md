# array-find-index
查找元素的索引，同 [findIndex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

## 来源
- [GitHub](https://github.com/sindresorhus/array-find-index)

## 使用
```js
const arrayFindIndex = require('array-find-index');

arrayFindIndex(['rainbow', 'unicorn', 'pony'], x => x === 'unicorn');
//=> 1
```

## 源码
```js
module.exports = function (arr, predicate, ctx) {
    // 检测是否支持 原生的 findIndex
	if (typeof Array.prototype.findIndex === 'function') {
		return arr.findIndex(predicate, ctx);
	}

	if (typeof predicate !== 'function') {
		throw new TypeError('predicate must be a function');
	}

	var list = Object(arr);
	var len = list.length;

	if (len === 0) {
		return -1;
	}
    // 调用给定函数，返回符合条件的第一个索引
	for (var i = 0; i < len; i++) {
		if (predicate.call(ctx, list[i], i, list)) {
			return i;
		}
	}

	return -1;
};
```