---
title: markdown 语法
date: 2016-12-24 16:31:35
tags: markdown
---

# 兼容HTML
``` html
//这是一个普通table。

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

//这是另一个普通table。
```

请注意，在 HTML 区块标签间的 Markdown 格式语法将不会被处理。比如，你在 HTML 区块内使用 Markdown 样式的*强调*会没有效果。

<!-- more -->

# 特殊字符自动转换


```js
4<5
```
Markdown 将会把它转换为：

```js
4 &lt; 5
```

# 语法

## 段落/换行
在插入处先按入两个以上的空格然后回车

## 标题
Markdown 支持两种标题的语法
#### 用底线的形式，利用 = （最高阶标题）和 - （第二阶标题），例如：
```html
This is an H1
=============

This is an H2
-------------
```
任何数量的 = 和 - 都可以有效果

#### 在行首插入 1 到 6 个 # ，对应到标题 1 到 6 阶，例如：
```html 
# 这是 H1

## 这是 H2

###### 这是 H6 
```

## 引用
在每行的最前面加上 >
Markdown 也允许你偷懒只在整个段落的第一行最前面加上 >
引用的区块内也可以使用其他的 Markdown 语法

```html 
> ## 这是一个标题。
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.
```
## 列表
Markdown 支持有序列表和无序列表。

无序列表使用星号、加号或是减号作为列表标记：

```html 
*   Red
*   Green
*   Blue 
```
有序列表则使用数字接着一个英文句点:

```html 
1.  Bird
2.  McHale
3.  Parish
```

列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：

```html 
*   This is a list item with two paragraphs.

    This is the second paragraph in the list item. You're
only required to indent the first line. Lorem ipsum dolor
sit amet, consectetuer adipiscing elit.

*   Another item in the same list.

```

## 代码
使用4个空格或者tab
	这是一个普通段落：

	这是一个代码区块。

或者使用反引号

## 分割线
```html 
	* * *

	***

	*****

	- - -

	---------------------------------------
```
****************


## 链接
Markdown中有两种方式，实现链接，分别为内联方式和引用方式。
```html 
内联方式：This is an [example link](http://example.com/).
引用方式：
I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].  

[1]: http://google.com/        "Google" 
[2]: http://search.yahoo.com/  "Yahoo Search" 
[3]: http://search.msn.com/    "MSN Search"
```
内联方式：This is an [example link](http://example.com/).
引用方式：
I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].  

[1]: http://google.com/        "Google" 
[2]: http://search.yahoo.com/  "Yahoo Search" 
[3]: http://search.msn.com/    "MSN Search"


## 自动链接
```html
<http://example.com/>
```
<http://example.com/>

## 图片
图片的处理方式和链接的处理方式，非常的类似。

```html 
内联方式：![alt text](https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png "Title")
引用方式：
![alt text][id] 

[id]: https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png "Title"
```
内联方式：![alt text](https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png "Title")
引用方式：
![alt text][id] 

[id]: https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png "Title"


## 强调

Markdown 使用星号（*）和底线（_）作为标记强调字词的符号，被 * 或 _ 包围的字词会被转成用 <em> 标签包围，用两个 * 或 _ 包起来的话，则会被转成 <strong>，例如：

```html 
*single asterisks*

_single underscores_

**double asterisks**

__double underscores__
```

你可以随便用你喜欢的样式，唯一的限制是，你用什么符号开启标签，就要用什么符号结束。
但是如果你的 * 和 _ 两边都有空白的话，它们就只会被当成普通的符号。
如果要在文字前后直接插入普通的星号或底线，你可以用反斜线