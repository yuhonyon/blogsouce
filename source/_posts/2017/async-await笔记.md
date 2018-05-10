layout: "post"
title: "async-await笔记"
date: "2017-11-23 16:04"
---

>`async-await`:`promise`和`generator`的语法糖

## 错误处理

使用try catch 之后我们就能够拿到 Promise.reject 回来的数据

```js
async function errorDemo() {
  try {
      let result = await outErrorFn();
      console.log(result);
  } catch (err) {
      console.log(err);
  }
}
```

## 并行处理

```js
//错误,并发的请求变成了阻塞式同步的操作了
async function bugDemo() {
    await fetchApi();
    await fetchApi();
    await fetchApi();
    console.log('清除loading');
}
```
```js
async function goodDemo() {
    let p1= fetchApi();
    let p2= fetchApi();
    let p3= fetchApi();
    await Promise.all([p1, p2, p3]);
    console.log('清除loading');
}
```

## for 循环

await必须在async函数的上下文中的

```js
async function forEachDemo() {
    let arr = [1, 2, 3, 4, 5];
    arr.forEach(item => {
        await item;//报错,await不在async的上下文中
    });
}
```

```js
async function forDemo() {
    let arr = [1, 2, 3, 4, 5];
    for (let i = 0; i < arr.length; i ++) {
        await arr[i];
    }
}
```
