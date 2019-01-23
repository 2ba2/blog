## 什么是递归？
程序调用自身的编程技巧称为递归（ recursion）。

构成递归需具备的条件：
- 化繁为简：子问题须与原始问题为同样的事，且更为简单；
- 出口：不能无限制地调用本身，须有个出口，化简为非递归状况处理。

以用 JavaScript 求解[斐波那契数列](https://baike.baidu.com/item/%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0%E5%88%97/99145)作为例子，了解递归。

斐波那契数列的递推关系：
![](https://img2018.cnblogs.com/blog/1164869/201901/1164869-20190123160045148-896442498.png)

JavaScript 代码实现：
```js
function fibonacci(n) {
    if (n === 0 || n === 1) {
        return n;  // 出口
    }
    return fibonacci(n - 1) + fibonacci(n - 2); // 化繁为简
}
```

通过对 `JavaScript` 代码进行 `Debug`，可以发现递归最重要的就是：1、化繁为简；2、出口。

化繁为简就是将问题分解；出口一定要有，如果没有出口或者调用层级过深都会导致 `stack overflow`。
![debug](https://img2018.cnblogs.com/blog/1164869/201901/1164869-20190123161304694-589973437.png)

---

## 什么是递归组件？
递归组件就是指组件在模板中调用自己。

递归都需要 化繁为简 和 出口 ，递归组件的化繁为简很简单，只需要指定组件的 `name` 属性即可；递归组件的出口也很简单，就是通过 `v-if` 指定递归的终点。

容器：
```html
<template>
  <div>
    <recursion :tree="tree"></recursion>
  </div>
</template>

<script>
import recursion from '@/components/VueDataStream/recursion.vue'
export default {
  name: 'HelloWorld',
  data () {
    return {
      tree: [{
        label: '一级 1',
        children: [{
          label: '二级 1-1',
          children: [{
            label: '三级 1-1-1',
            children: [{
              label: '四级 1-1-1'
            }]
          }]
        }]   
      }]
    }
  },
  components: {
    recursion
  }
}
</script>
```

递归组件：
```html
<template>
  <ul>
    <li v-for="item in tree" :key="item.label">
      <div>{{item.label}}</div>
      <recursion v-if="item.children" :tree="item.children"></recursion>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'recursion',
  props: {
    tree: {
      type: Array,
      default: () => []
    }
  }
}
</script>
```

---

## 递归组件有什么用？
Tree 树形控件

<iframe width="100%" height="300" src="//jsfiddle.net/sksst/whosyt98/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

Cascader 级联选择器
<iframe width="100%" height="300" src="//jsfiddle.net/sksst/rf5k9pjb/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

## 参考
- [递归组件](https://cn.vuejs.org/v2/guide/components-edge-cases.html#%E9%80%92%E5%BD%92%E7%BB%84%E4%BB%B6)
- [tree-node](https://github.com/ElemeFE/element/blob/dev/packages/tree/src/tree-node.vue)

