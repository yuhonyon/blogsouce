layout: "post"
title: "常用babel-plugin"
date: "2018-05-03 17:36"
---

*** 注意:presets是倒叙 plugins是正序 ***



# transform-function-bind

>函数绑定'::'

安装:
```bash
  cnpm i babel-plugin-transform-function-bind -D
```
配置:
```json
"plugins": ["transform-function-bind"]
```
例子:
```js
obj::func
// 相当于：
func.bind(obj)

::obj.func
// 相当于：
obj.func.bind(obj)

obj::func(val)
// 相当于：
func.call(obj, val)

::obj.func(val)
// 相当于：
obj.func.call(obj, val)

```




# transform-do-expressions

>解析do{}表达式,主要应用jsx

安装:
```bash
  cnpm i babel-plugin-transform-do-expressions -D
```
配置:
```json
"plugins": ["transform-do-expressions"]
```
例子:
```jsx
const Component = props =>
  <div className='myComponent'>
    {do {
      if(color === 'blue') { <BlueComponent/>; }
      else if(color === 'red') { <RedComponent/>; }
      else if(color === 'green') { <GreenComponent/>; }
    }}
  </div>
```


# transform-es2015-modules-commonjs

>转es6 modules 为commonjs模式

安装:
```bash
  cnpm i babel-plugin-transform-es2015-modules-commonjs -D
```
配置:
```json
"plugins": ["transform-es2015-modules-commonjs"]
```



# transform-async-to-generator

>解析async

安装:
```bash
  cnpm i babel-plugin-transform-async-to-generator -D
```
配置:
```json
"plugins": ["transform-async-to-generator"]
```




# transform-export-extensions

>解析export-from

安装:
```bash
  cnpm i babel-plugin-transform-export-extensions -D
```
配置:
```json
"plugins": ["transform-export-extensions"]
```
例子:
```js
export * as ns from 'mod';
export v from 'mod';
```


# transform-decorators-legacy

>解析修饰器（Decorator）

安装:
```bash
  cnpm i babel-plugin-transform-decorators-legacy -D
```
配置:
```json
"plugins": ["transform-decorators-legacy"]
```


# transform-class-properties

>class 静态属性&&初始属性

安装:
```bash
  cnpm i babel-plugin-transform-class-properties -D
```
配置:
```json
"plugins": ["transform-class-properties"]
```
例子:
```js
class Bork {
    //Property initializer syntax
    instanceProperty = "bork";
    boundFunction = () => {
      return this.instanceProperty;
    }

    //Static class properties
    static staticProperty = "babelIsCool";
    static staticFunction = function() {
      return Bork.staticProperty;
    }
  }

  let myBork = new Bork;

  //Property initializers are not on the prototype.
  console.log(myBork.prototype.boundFunction); // > undefined

  //Bound functions are bound to the class instance.
  console.log(myBork.boundFunction.call(undefined)); // > "bork"

  //Static function exists on the class.
  console.log(Bork.staticFunction()); // > "babelIsCool"
```
