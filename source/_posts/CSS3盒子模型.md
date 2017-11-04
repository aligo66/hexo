---
title: CSS3盒子模型
date: 2017-04-18 12:28:18
tags: CSS3
---
## CSS3盒子模型

### CSS盒模型
CSS中有一种基础设计模式叫盒模型，盒模型定义了Web页面中的元素中如何来解析。CSS中每一个元素都是一个盒模型，包括html和body标签元素。在盒模型中主要包括width、height、border、background、padding和margin这些属性，而且他们之间的层次关系可以相互影响，来看一张盒模型的3D展示图：

<img src="http://ww4.sinaimg.cn/large/006tKfTcgy1feqq1z8wp9j30hn0epn37.jpg" width=350px height=300px>

从图中可以看出padding属性和content属性层叠background-image属性，层叠background-color属性，这个是存在的，它们四者之间构成了Ｚ轴（垂直屏幕的坐标）多重层叠关系。但是border属性与margin属性、padding属性三者之间应该是平面上的并级关系，并不能构成Ｚ轴的层叠关系。
<!-- more -->
在CSS3中新增加了box-sizing属性，能够事先定义盒模型的尺寸解析方式，其语法规则如下：

box-sizing: content-box | border-box | inherit

取值说明

属性值　　　　　　　　　　　　　　　　　　属性值说明

content-box

默认值，其让元素维持W3C的标准盒模型，也就是说元素的宽度和高度（width/height）等于元素边框宽度（border）加上元素内距（padding）加上元素内容宽度或高度（content width/ height），也就是element width/height = border + padding + content width / height

border-box

重新定义CSS2.1中盒模型组成的模式，让元素维持IE传统的盒模型（IE6以下版本和IE6-7怪异模式），也就是说元素的宽度或高度等于元素内容的宽度或高度。从上面盒模型介绍可知，这里的内容宽度或高度包含了元素的border、padding、内容的宽度或高度（此处的内容宽度或高度＝盒子的宽度或高度—边框—内距）。

inherit

使元素继承父元素的盒模型模式

### 一、Flex布局
Flex是Flexible Box的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。
任何一个容易都可以指定为Flex布局。

```
.box {
	display: flex;
}
```
行内元素也可以使用Flex布局

```
.box {
	display:inline-flex;
}
```
Wevkit内核的浏览器，必须加上-webkit前缀

```
.box {
	display: -webkit-flex;    /*safari*/
	display: flex;
}

```
注意，设为Flex布局以后，子元素的float、clear和vertical-align属性将失效

### 二、基本概念
采用Flex布局的元素，称为Flex容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称"项目"。
器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。
项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

### 三、容器的属性
以下6个属性设置在容器上

```
. flex-directionn
. flex-wrap
. flex-flow
. justify-content
. align-items
. align-content

```
#### 3.1 flex-direction属性
flex-direction 属性决定主轴的方向 (即项目的排列方向)。

```
.box {
	flex-direction: row | row-reverse | column | column-reverse
}

```
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071005.png" alt="" title="">
它可能有4个值。

```
. row (默认值): 主轴为水平方向，起点在左端。
. row-reverse: 主轴为水平方向，起点在右端
. column: 主轴为垂直方向，起点在上沿
. column-reverse: 主轴为垂直方向，起点在下沿


```
#### 3.2 flex-wrap 属性
默认情况下，项目都排在一条线上(又称为轴线)上。flex-wrap属性定义，如果一条轴线上，如何换行。
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071006.png" alt="" title="">

```
.box {
	flex-wrap: nowrap | wrap | wrap-reverse;
}

```
它可能取三个值
1.nowrap(默认): 不换行。
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071007.png" alt="" title="">
2.wrap:换行，第一行在上方。
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071008.jpg" alt="" title="">
3.wrap-reverse: 换行，第一行在下方。
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071009.jpg" alt="" title="">

#### 3.3 flex-flow
flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

```
.box {
	flex-flow: <flex-direction> || <flex-wrap>;
}
```
#### 3.4 justify-content属性
justify-content属性定义了项目在主轴上的对齐方式。

```
.box {
	justify-content: flex-start | flex-end | center | space-between|space-around;
}

```
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071010.png" alt="" title="">
它可能取5个值，具体对齐方式与轴的方向有关。下面假设主轴为从左到右。

```
. flex-start(默认值) : 左对齐
. flex-end: 右对齐
. center: 居中
. space-between: 两端对齐，项目之间的间隔都相等
. space-around: 每个项目两侧的间隔相等，所以，项目之间的间隔比项目与边框的间隔大一倍
```

#### 3.5 align-items属性
align-items属性定义项目子啊交叉轴上如何对齐。

```
.box {
	align-items: flex-start | flex-end | center | baseline | stretch;
}

```
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071011.png" alt="" title="">
它可能取5个值，具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下。

```
. flex-start: 交叉值得起点对齐
. flex-end: 交叉轴的终点对齐。
. center: 交叉轴的中点对齐。
. basseline: 项目的第一行文字的基线对齐。
. stretch(默认值) : 如果项目末设置高度或设置为auto,将占满整个容器的高度。
```
#### 3.6 align-content属性
align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
.box {
	align-content: flex-strat | flex-end | center | space-between | space-around | stretch;
}
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071012.png" alt="" title="">
该属性可能取6个值。

```
flex-start：与交叉轴的起点对齐。
flex-end：与交叉轴的终点对齐。
center：与交叉轴的中点对齐。
space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
stretch（默认值）：轴线占满整个交叉轴。

```
### 四、项目的属性
以下6个属性设置在项目上。

```
order
flex-grow
flex-shrink
flex-basis
flex
align-self

```
#### 4.1 order属性
```
.item {
  order: <integer>;
}
```
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071013.png" alt="" title="">

#### 4.2 flex-grow属性
flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

```
.item {
	flex-grow: <number>; /默认为0/
}

```
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071014.png" alt="" title="">
如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

#### 4.3 felx-shrink属性
flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

```
.item {
	flex-shrink: <number> /默认为1/
}
```
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071015.jpg" alt="" title="">
如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。

#### 4.4 flex-basis属性
flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

```
.item {
  flex-basis: <length> | auto; /* default auto */
}
```
它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。

#### 4.5 flex属性
flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

```
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```
该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。

#### 4.6 align-self属性
align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

```
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```
<img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071016.png" alt="" title="">
该属性可能取6个值，除了auto，其他都与align-items属性完全一致。
