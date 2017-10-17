layout: "post"
title: "数据绑定Proxy VS Object.definProperty"
date: "2017-10-16 11:32"
---
## Object.defineProperty

`Object.defineProperty(obj, prop, descriptor)`
> Object.defineProperty() 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性， 并返回这个对象 [详情](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)

### 参数
**obj**
需要被操作的目标对象

**prop**
目标对象需要定义或修改的属性的名称。

**descriptor**
将被定义或修改的属性的描述符。

**返回值**
被传递给函数的对象。

```js
let aa={age:11}
Object.defineProperty(ironman, 'age', {
  set (val) {
    element.innerHTML=`这sb今年${age}岁了`
    return val
  }
})
```
使用set()方法去监测属性变化，但是对于一个数组使用value()方法来代替

## Proxy
`var proxy = new Proxy(target, handler);`

>Proxy 用于修改某些操作的默认行为，等同于在语言层面做出修改，所以属于一种“元编程”（meta programming），即对编程语言进行编程。[详情](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy)

### 参数
**target**
一个目标对象(可以是任何类型的对象，包括本机数组，函数，甚至另一个代理)用Proxy来包装。

**handler**
一个对象，其属性是当执行一个操作时定义代理的行为的函数

```js
let aa={age:23}
let proxy = new Proxy(aa, {
  set (target, property, value) {
    target[property] = value
    element.innerHTML=`这sb今年${age}岁了`
    return true
  }
})
```

## 实例
```js
class Vue{
  constructor(options){
    this.$data=options.data;
    this.$el=options.el;
    this.$template=options.template;
    this._render(this.$template,this.$data)
  }
  $setData (dataObj, fn) {
    let self = this
    let once = false
    let $d = new Proxy(dataObj, {
      set (target, property, value) {
        if (!once) {
          target[property] = value
          once = true
          self._render(self.$template, self.$data)
        }
        return true
      }
    })
    fn($d)
  }

  _render (tplString, data) {
    this.$el.innerHTML = this._replaceFun(tplString, data)
  }

  _replaceFun(str, data) {
    let self = this
    return str.replace(/{{([^{}]*)}}/g, (a, b) => {
      let r = self._getObjProp(data, b);
      if (typeof r === 'string' || typeof r === 'number') {
        return r
      } else {
        return self._getObjProp(r, b.split('.')[1])
      }
    })
  }

  _getObjProp (obj, propsName) {
    let propsArr = propsName.split('.')
    function rec(o, pName) {
      if (!o[pName] instanceof Array && o[pName] instanceof Object) {
        return rec(o[pName], propsArr.shift())
      }
      return o[pName]
    }
    return rec(obj, propsArr.shift())
  }
}
```

## 例子
```html
<div id="app">
  <p>这sb今年{{age}}岁了</p>
  <input type="text" id="input">
</div>
<script>
  let template=document.querySelector('#app').innerHTML
  let vue=new Vue({
    template:template,
    el:document.querySelector('#app'),
    data:{
      age:24
    }
  })
  document.querySelector('#input').oninput = (e) => {
  vue.$setData(vue.$data, ($d) => {
    $d.age = e.target.value
  })
}
</script>
```
