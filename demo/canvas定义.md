## canvas定义

**<canvas> **是 [HTML5](https://developer.mozilla.org/zh-CN/docs/HTML/HTML5) 新增的元素，可用于通过使用[JavaScript](https://developer.mozilla.org/zh-CN/docs/JavaScript)中的脚本来绘制图形。例如，它可以用于绘制图形，制作照片，创建动画，甚至可以进行实时视频处理或渲染。

## 一、基本用法

`<canvas></canvas>`

1. 使用 canvas 标签, 即可在页面中开辟一格区域. 可以设置其 width 和 height 设置该区域的尺寸.

2. 默认 canvas 的宽高为 300 和 150.

3. ##### 不要使用 CSS 的方式设置宽高, 应该使用 HTML 属性.

4. 如果浏览器不支持 canvas 标签, 那么就会将其解释为 div 标签. 因此常常在 canvas 中嵌入文本, 以提示用户浏览器的能力.

5. canvas 的兼容性非常强, 只要支持该标签的, 基本功能都一样, 因此不用考虑兼容性问题.

6. canvas 本身不能绘图. 是使用 JavaScript 来完成绘图. canvas 对象提供了各种绘图用的 api.

7. 绘制矩形、清除矩形区域、圆弧、路径、绘制线段、绘制贝塞尔曲线、线性渐变、径向渐变（发散）、图形变形（平移、旋转、缩放）、矩阵变换（图形变形的机制）、图形组合、给图形绘制阴影、绘制图像（图片平铺、裁剪、像素处理[不只图像、包括其他绘制图形]）、绘制文字、保存和恢复状态（context）、保存文件

## 二、基本API

#### 绘制直线

| 名称                                       | 备注                             |
| :--------------------------------------- | ------------------------------ |
| beginPath()                              | 新建一条路径，生成之后，图形绘制命令被指向到路径上生成路径。 |
| closePath()                              | 闭合路径之后图形绘制命令又重新指向到上下文中。        |
| stroke()                                 | 通过线条来绘制图形轮廓。                   |
| strokeStyle                              | 设置线条的样式（颜色）                    |
| fill()                                   | 通过填充路径的内容区域生成实心的图形。            |
| fillStyle                                | 设置填充样式（颜色）                     |
| moveTo(*x*, *y*)                         | 将笔触移动到指定的坐标x以及y上               |
| [`lineTo(x, y)`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineTo) | 绘制一条从当前位置到指定x以及y位置的直线。         |

####  绘制矩形

| 名称                                       | 备注                 |
| :--------------------------------------- | ------------------ |
| [`fillRect(x, y, width, height)`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/fillRect) | 绘制一个填充的矩形          |
| [`strokeRect(x, y, width, height)`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/strokeRect) | 绘制一个矩形的边框          |
| [`clearRect(x, y, width, height)`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/clearRect) | 清除指定矩形区域，让清除部分完全透明 |

#### 绘制圆

| 名称                                       | 备注                                       |
| :--------------------------------------- | ---------------------------------------- |
| [`arc(x, y, radius, startAngle, endAngle, anticlockwise)`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/arc) | 画一个以（x,y）为圆心的以radius为半径的圆弧（圆），从startAngle开始到endAngle结束，按照anticlockwise给定的方向（默认为顺时针）来生成。 |
| [`arcTo(x1, y1, x2, y2, radius)`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/arcTo) | 根据给定的控制点和半径画一段圆弧，再以直线连接两个控制点。            |

#### 变换

| 名称                | 备注                                       |
| ----------------- | :--------------------------------------- |
| translate( x, y ) | 该方法将坐标进行平移.  x 表示水平移动, 正数向右, 负数向左.  y 表示垂直移动, 正数向下, 负数向上.  变换可以重复调用, 变换是可以累加的. |
| rotate( radian )  | 该方法将坐标轴进行旋转变换.  参数是弧度, 表示旋转的方式. 正数表示顺时针旋转, 负数表示逆时针旋转. |
| scale( x, y )     | 该方法实现水平与垂直的缩放.  参数 x 控制水平缩放倍率. 传参 1 表示不作缩放, 传入大于 1 的数字表示扩大.  参数 y 控制垂直缩放倍率. 传参 1 表示不作缩放, 传入大于 1 的数字表示扩大. |



#### getContext 方法

语法：Canvas.getContext( typeStr )

描述:

1. 该方法用于绘制上下文工具.
2. 如果是绘制平面图形使用 `'2d'` 作为参数, 如果绘制立体图形使用 `'webgl'`.
3. 使用 `'2d'` 返回 `CanvasRenderingContext2D` 类型的对象.
4. 使用 `'webgl'` 返回 `WebGLRenderingContext` 类型的对象.

#### globalCompositeOperation属性

解释：指定后续的图形与画布上已有图形的覆盖方式，共有11种

| source-over        | 默认。在目标图像上显示源图像。                        |
| ------------------ | -------------------------------------- |
| source-atop        | 在目标图像顶部显示源图像。源图像位于目标图像之外的部分是不可见的。      |
| source-in          | 在目标图像中显示源图像。只有目标图像内的源图像部分会显示，目标图像是透明的。 |
| source-out         | 在目标图像之外显示源图像。只会显示目标图像之外源图像部分，目标图像是透明的。 |
| destination-over   | 在源图像上方显示目标图像。                          |
| destination-atop   | 在源图像顶部显示目标图像。源图像之外的目标图像部分不会被显示。        |
| destination++++-in | 在源图像中显示目标图像。只有源图像内的目标图像部分会被显示，源图像是透明的。 |
| destination-out    | 在源图像外显示目标图像。只有源图像外的目标图像部分会被显示，源图像是透明的。 |
| lighter            | 显示源图像 + 目标图像。                          |
| copy               | 显示源图像。忽略目标图像。                          |
| xor                | 使用异或操作对源图像与目标图像进行组合。                   |

![5D7CD8E3-7E5B-476A-8B23-C1D3CF46F7D5](/Users/wangjing/Library/Containers/com.tencent.qq/Data/Library/Application Support/QQ/Users/897527394/QQ/Temp.db/5D7CD8E3-7E5B-476A-8B23-C1D3CF46F7D5.png)

#### 运用

（1）刮刮乐

## 三、Image处理

####  1.drawImage()方法

是 Canvas 2D API 中的方法，它提供了多种方式来在Canvas上绘制图像。

语法：ctx.drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight)

参数： 

1.image绘制到上下文的元素。允许任何的 canvas 图像源(CanvasImageSource)，例如：HTMLImageElement，HTMLVideoElement，或者 HTMLCanvasElement。
2.dx目标画布的左上角在目标canvas上 X 轴的位置。
3.dy目标画布的左上角在目标canvas上 Y 轴的位置。
4.dWidth在目标画布上绘制图像的宽度。 允许对绘制的图像进行缩放。 如果不说明， 在绘制时图片宽度不会缩放。
5.dHeight在目标画布上绘制图像的高度。 允许对绘制的图像进行缩放。 如果不说明， 在绘制时图片高度不会缩放。
6.sx需要绘制到目标上下文中的，源图像的矩形选择框的左上角 X 坐标。
7.sy需要绘制到目标上下文中的，源图像的矩形选择框的左上角 Y 坐标。
8.sWidth需要绘制到目标上下文中的，源图像的矩形选择框的宽度。如果不说明，整个矩形从坐标的sx和sy开始，到图像的右下角结束。
9.sHeight需要绘制到目标上下文中的，源图像的矩形选择框的高度。

![Canvas_drawimage](/Users/wangjing/Downloads/Canvas_drawimage.jpg)

#### 2.ImageData对象

[`ImageData`](https://developer.mozilla.org/zh-CN/docs/Web/API/ImageData)对象中存储着canvas对象真实的像素数据

[`ImageData.data`](https://developer.mozilla.org/zh-CN/docs/Web/API/ImageData/data) [Uint8ClampedArray`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Uint8ClampedArray) 描述了一个一维数组，包含以 RGBA 顺序的数据，数据使用  `0` 至 `255`（包含）的整数表示。

[`ImageData.height`](https://developer.mozilla.org/zh-CN/docs/Web/API/ImageData/height) 无符号长整型（`unsigned` `long`），使用像素描述 **ImageData** 的实际高度。

[`ImageData.width`](https://developer.mozilla.org/zh-CN/docs/Web/API/ImageData/width) 无符号长整型（`unsigned` `long`），使用像素描述 **ImageData** 的实际宽度。

#### 3.getImageData()方法

返回一个[`ImageData`](https://developer.mozilla.org/zh-CN/docs/Web/API/ImageData)对象，用来描述canvas区域隐含的像素数据，这个区域通过矩形表示，起始点为*(sx, sy)、*宽为*sw、*高为*sh*

语法：Canvas.getImageData(x, sy, sw, sh);

#### 4.createImageData()方法

是 Canvas 2D API 创建一个 新的、空白的、指定大小的 [`ImageData`](https://developer.mozilla.org/zh-CN/docs/Web/API/ImageData) 对象。 所有的像素在新对象中都是透明的。

语法：ctx.createImageData(width, height);

​	 ctx.createImageData(imagedata);

#### 5.putImageData()方法

是 Canvas 2D API 将数据从已有的 [`ImageData`](https://developer.mozilla.org/zh-CN/docs/Web/API/ImageData) 对象绘制到位图的方法。 如果提供了脏矩形，只能绘制矩形的像素

语法：ctx.putImageData(imagedata, dx, dy, dirtyX, dirtyY, dirtyWidth, dirtyHeight)

参数：

1.imageData包含像素值的数组对象。

2.dx源图像数据在目标画布中的位置偏移量（x 轴方向的偏移量）。

3.dy源图像数据在目标画布中的位置偏移量（y 轴方向的偏移量）。

4.dirtyX 可选在源图像数据中，矩形区域左上角的位置。默认是整个图像数据的左上角（x 坐标）。

5.dirtyY 可选在源图像数据中，矩形区域左上角的位置。默认是整个图像数据的左上角（y 坐标）。

6.dirtyWidth 可选在源图像数据中，矩形区域的宽度。默认是图像数据的宽度。

7.dirtyHeight可选在源图像数据中，矩形区域的高度。默认是图像数据的高度

![E1075BA6-1CA2-44A2-A04D-F8EA7E77D064](/Users/wangjing/Library/Containers/com.tencent.qq/Data/Library/Application Support/QQ/Users/897527394/QQ/Temp.db/E1075BA6-1CA2-44A2-A04D-F8EA7E77D064.png)

#### 6.运用

（1）照片灰度和反色

（2）照片格栅

（3）生成base64水印图片

## 四、基本运动

1.圆周运动

2.碰撞与反弹

3.自由落体

4.背景图

