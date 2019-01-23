# dayjs
Day.js 是一个轻量的处理时间和日期的 JavaScript 库，和 Moment.js 的 API 设计保持完全一样. 如果您曾经用过 Moment.js, 那么您已经知道如何使用 Day.js

## 来源
- [dayjs](https://github.com/iamkun/dayjs)
- [npm](https://www.npmjs.com/package/dayjs)

## 特点
* 🕒 和 Moment.js 相同的 API 和用法
* 💪 不可变数据 (Immutable)
* 🔥 支持链式操作 (Chainable)
* 🌐 国际化 I18n
* 📦 仅 2kb 大小的微型库
* 👫 全浏览器兼容

## 示例
```js
dayjs('2018-08-08') // 解析

dayjs().format('{YYYY} MM-DDTHH:mm:ss SSS [Z] A') // 展示

dayjs().set('month', 3).month() // 获取

dayjs().add(1, 'year') // 处理

dayjs().isBefore(dayjs()) // 查询
```

<iframe height="265" style="width: 100%;" scrolling="no" title="dayjs" src="//codepen.io/2ba2/embed/zeYvyj/?height=265&theme-id=0&default-tab=html,resultundefined" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/2ba2/pen/zeYvyj/'>dayjs</a> by 2ba2
  (<a href='https://codepen.io/2ba2'>@2ba2</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

## 参考
- [安装指南](https://github.com/iamkun/dayjs/blob/dev/docs/zh-cn/Installation.md)
- [API参考](https://github.com/iamkun/dayjs/blob/dev/docs/zh-cn/API-reference.md)

