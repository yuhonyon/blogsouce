---
title: markdown 语法
date: 2016-12-14 16:31:35
tags: markdown
---


# <canvas> 
``` html
<canvas id="canvas" width="100" height="100">该浏览器不支持canvas</canvas>
```

* 没有设置`width`,`height`canvas会初始化宽度为300像素和高度为150像素。
* 使用CSS设置宽高,canvas会伸缩(类似`<img>`)
* `<canvas>`标签中提供了替换内容。支持`<canvas>`的浏览器将会忽略在容器中包含的内容，并且只是正常渲染`canvas`。

# Context
2d渲染上下文方式
```js
var canvas = document.getElementById('canvas');
var ctx = canvas.getContext('2d');
```

# 绘制API

## 矩形
```js
CanvasRenderingContext2D.fillRect(x, y, width, height)
//绘制一个填充的矩形
CanvasRenderingContext2D.strokeRect(x, y, width, height)
//绘制一个矩形的边框
CanvasRenderingContext2D.clearRect(x, y, width, height)
//清除指定矩形区域，让清除部分完全透明。
```

## 路径
```
CanvasRenderingContext2D.beginPath()
//新建一条路径，生成之后，图形绘制命令被指向到路径上生成路径。
CanvasRenderingContext2D.closePath()
//闭合路径之后图形绘制命令又重新指向到上下文中。
CanvasRenderingContext2D.moveTo()
//将一个新的子路径的起始点移动到(x，y)坐标。
CanvasRenderingContext2D.lineTo()
//使用直线连接子路径的最后的点到x,y坐标。
CanvasRenderingContext2D.bezierCurveTo()
//添加一个3次贝赛尔曲线路径。该方法需要三个点。 第一、第二个点是控制点，第三个点是结束点。起始点是当前路径的最后一个点，绘制贝赛尔曲线前，可以通过调用 moveTo() 进行修改。
CanvasRenderingContext2D.quadraticCurveTo()
//添加一个2次贝赛尔曲线路径。
CanvasRenderingContext2D.arc()
//绘制一段圆弧路径， 圆弧路径的圆心在 (x, y) 位置，半径为 r ，根据anticlockwise （默认为顺时针）指定的方向从 startAngle 开始绘制，到 endAngle 结束。
CanvasRenderingContext2D.arcTo()
//根据控制点和半径绘制圆弧路径，使用直线连接前一个点。
CanvasRenderingContext2D.ellipse() 
//添加一个椭圆路径，椭圆的圆心在（x,y）位置，半径分别是radiusX 和 radiusY ，按照anticlockwise （默认顺时针）指定的方向，从 startAngle  开始绘制，到 endAngle 结束。
CanvasRenderingContext2D.rect()
//创建一个矩形路径，矩形的起点位置是 (x, y) ，尺寸为 width 和 height。
CanvasRenderingContext2D.stroke()
//通过线条来绘制图形轮廓。
CanvasRenderingContext2D.fill()
//通过填充路径的内容区域生成实心的图形。
```

## 文本
```
CanvasRenderingContext2D.fillText()
//在(x,y)位置绘制（填充）文本。
CanvasRenderingContext2D.strokeText()
//在(x,y)位置绘制（描边）文本。
CanvasRenderingContext2D.measureText()
//返回 TextMetrics 对象。
```

## 图片
```
CanvasRenderingContext2D.drawImage()
//绘制指定的图片。该方法有多种格式，提供了很大的使用灵活性。
```

# 样式API
## 线样式
```
CanvasRenderingContext2D.lineWidth
线的宽度。默认 1.0
CanvasRenderingContext2D.lineCap
线末端的类型。 允许的值： butt (默认), round, square.
CanvasRenderingContext2D.lineJoin
定义两线相交拐点的类型。允许的值：round, bevel, miter(默认)。
CanvasRenderingContext2D.miterLimit
斜接面限制比例。默认 10。
CanvasRenderingContext2D.getLineDash()
返回当前线段样式的数组，数组包含一组数量为偶数的非负数数字。
CanvasRenderingContext2D.setLineDash()
设置当前的线段样式。
CanvasRenderingContext2D.lineDashOffset
描述在哪里开始绘制线段。
```

## 文本样式
```
CanvasRenderingContext2D.font
字体设置。 默认值 10px sans-serif。
CanvasRenderingContext2D.textAlign
文本对齐设置。 允许的值： start (默认), end, left, right 或 center.
CanvasRenderingContext2D.textBaseline
基线对齐设置。 允许的值： top, hanging, middle, alphabetic (默认),ideographic, bottom.
CanvasRenderingContext2D.direction
文本的方向。 允许的值： ltr, rtl, inherit (默认).
```

## 填充,描边,渐变,图案
```
CanvasRenderingContext2D.fillStyle
//图形内部的颜色和样式。 默认 #000 (黑色).
CanvasRenderingContext2D.strokeStyle
//图形边线的颜色和样式。 默认 #000 (黑色)
CanvasRenderingContext2D.createLinearGradient()
//创建一个沿着参数坐标指定的线的线性渐变。
CanvasRenderingContext2D.createRadialGradient()
//创建一个沿着参数坐标指定的线的放射性性渐变。
CanvasRenderingContext2D.createPattern()
//使用指定的图片 (CanvasImageSource)创建图案。通过 repetition 变量指定的方向上重复源图片。此方法返回 CanvasPattern对象。
```

## 阴影
```
CanvasRenderingContext2D.shadowBlur
//描述模糊效果。 默认 0
CanvasRenderingContext2D.shadowColor
//阴影的颜色。 默认fully-transparent black.
CanvasRenderingContext2D.shadowOffsetX
//阴影水平方向的偏移量。 默认 0.
CanvasRenderingContext2D.shadowOffsetY
//阴影垂直方向的偏移量。 默认 0.
```

# 方法API

## canvas状态
```
CanvasRenderingContext2D.save()
//使用栈保存当前的绘画样式状态，你可以使用 restore() 恢复任何改变。
CanvasRenderingContext2D.restore()
//恢复到最近的绘制样式状态，此状态是通过 save() 保存到”状态栈“中最新的元素。
CanvasRenderingContext2D.canvas
//对 HTMLCanvasElement 只读的反向引用。如果和 <canvas> 元素没有联系，可能为null。
```
## 路径
```
CanvasRenderingContext2D.drawFocusIfNeeded()
如果给定的元素获取了焦点，那么此方法会在当前的路径绘制一个焦点。
CanvasRenderingContext2D.scrollPathIntoView()
将当前或给定的路径滚动到窗口。
CanvasRenderingContext2D.clip()
从当前路径创建一个剪切路径。在  clip() 调用之后，绘制的所有信息只会出现在剪切路径内部。
CanvasRenderingContext2D.isPointInPath()
判断当前路径是否包含检测点。
CanvasRenderingContext2D.isPointInStroke()
判断检测点是否在路径的描边线上。
```

## 变换
在 CanvasRenderingContext2D 渲染背景中的对象会有一个当前的变换矩阵，一些方法可以对其进行控制。当创建当前的默认路径，绘制文本、图形和Path2D对象的时候，会应用此变换矩阵。
```
CanvasRenderingContext2D.currentTransform
//当前的变换矩阵 (SVGMatrix 对象)。
CanvasRenderingContext2D.rotate()
//在变换矩阵中增加旋转，角度变量表示一个顺时针旋转角度并且用弧度表示。
CanvasRenderingContext2D.scale()
//根据 x 水平方向和 y 垂直方向，为canvas 单位添加缩放变换。
CanvasRenderingContext2D.translate()
//通过在网格中移动 canvas 和 canvas 原点 x 水平方向、原点 y 垂直方向，添加平移变换
CanvasRenderingContext2D.transform()
//使用方法参数描述的矩阵多次叠加当前的变换矩阵。
CanvasRenderingContext2D.setTransform()
//重新设置当前的变换为单位矩阵，并使用同样的变量调用 transform() 方法。
CanvasRenderingContext2D.resetTransform() 
//使用单位矩阵重新设置当前的变换。
```

## 像素控制
```
CanvasRenderingContext2D.createImageData()
//使用指定的尺寸，创建一个新的、空白的 ImageData 对象。所有的像素在新对象中都是透明的。
CanvasRenderingContext2D.getImageData()
//返回一个 ImageData 对象，用来描述canvas区域隐含的像素数据，这个区域通过矩形表示，起始点为(sx, sy)、宽为sw、高为sh。
CanvasRenderingContext2D.putImageData()
//将数据从已有的 ImageData 绘制到位图上。 如果提供了脏矩形，只能绘制矩形的像素。 
```

## 图像
```
CanvasRenderingContext2D.imageSmoothingEnabled 
图像平滑的方式；如果禁用，缩放时，图像不会被平滑处理。
```