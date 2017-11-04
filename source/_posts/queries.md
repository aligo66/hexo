layout: media
title: media quires 媒体查询
date: 2017-04-18 15:05:00
tags: CSS3
---
### Media queries ——媒体类型 
　　在实际媒体类型有近十种之多，实际之中常用的也就那么几种，不过媒体类型的引用方法也有很多种，常见的有: link标签、@import 和 CSS3新增的@media几种
　　
### link方法
link方法引入媒体类型其实就是在<link>标签引用样式的时候，通过link标签中的media属性来指定不同的媒体类型。如下所示。

```
<link rel="stylesheet" type="text/css" href="style.css" media="screen" />
<link rel="stylesheet" type="text/css" href="print.css" media="print" />

```
<!--more -->

### @import方法
@import可以引用样式文件，同样也可以引用媒体类型，@import引入媒体类型主要用两种方式，一种在样式中通过@import调用另一个样式文件，另一种方法是在<head></head>标签中的<style></style>中引入。
如样式文件中调用另一个样式文件时，就可以指定对应的媒体类型。


@import url(reset.css) screen;   
@import url(print.css) print;


在<head>中<的style>标签中引入媒体类型方法.

<head>
<style type="text/css">
    @importurl(style.css) all;
</style>
</head>

 

@media方法

@media是CSS3中新引进的一个特性，被称为媒体查询。在页面中也可以通过这个属性来引入媒体类型。@media引入媒体类型和@import有点类似也具有两方式。

1.在样式文件中引入媒体类型

@media screen {
   选择器{/*你的样式代码写在这里…*/}
}

2.使用@media引入媒体类型的方式是在head标签中的style中引用。

<head>
<style type="text/css">
    @media screen{
    选择器{/*你的样式代码写在这里…*/}
}
</style>
</head>


### Media Queries 使用方法
Media Queries能在不同的条件下使用不同的样式，使页面在不同在终端设备下达到不同的渲染效果。前面简单的介绍了Media Queries如何引用到项目中，但Media Queries有其自己的使用规则。具体来说,Media Queries的使用方法如下。


@media 媒体类型and （媒体特性）{你的样式}


注意：使用Media Queries必须要使用“@media”开头，然后指定媒体类型（也可以称为设备类型），随后是指定媒体特性（也可以称之为设备特性）。媒体特性的书写方式和样式的书写方式非常相似，主要分为两个部分，第一个部分指的是媒体特性，第二部分为媒体特性所指定的值，而且这两个部分之间使用冒号分隔。例如：


(max-width: 480px)


从前面表中可以得知，主要有十种媒体类型和13种媒体特性，将其组合就类似于不同的CSS集合。但与CSS属性不同的是，媒体特性是通过min/max来表示大于等于或小于做为逻辑判断，而不是使用小于（<）和大于（>）这样的符号来判断。接下来一起来看看Media Queries在实际项目中常用的方式。

### 1.最大宽度max-width
"max-width"是媒体特性中最常用的一个特性，其意思是指媒体类型小于或等于指定的宽度时，样式生效。如:

@media screen and (max-width:480px) {
	.ads {
		display:none;
	 }
}


上面表示的是，当屏幕小于或等于480px，页面中的广告区块(.ads)将都被隐藏。

### 2.最小宽度 min-width
"min-width"与"max-width"相反，指的是媒体类型大于或等于指定宽度时，样式生效。

```
@meida screen and (min-width:900px;) {
	.wrapper{width: 980px;}
}

```
上面表示的是:当屏幕大于或等于900px时，容器".wrapper"的宽度为980px;


### 3.多个媒体特性使用
Media Queries 可以使用关键词"and"将多个媒体特性结合在一起，也就是说，一个Media Query可以包含0到多个表达式，表达式又可以包含0到多个关键字，以及一种媒体类型。
当屏幕在600px-900px之间时，body的背景色渲染为"#f5f5f5"，如下所示.

```
@media screen and (min-width:600px) and (max-width:900px;){
	body {background-color: #f5f5f5;}
}

```
### 4.设备屏幕的输出宽度Device Width
在智能设备上，例如iPhone、iPad等，还可以根据屏幕设备的尺寸来设置相应的样式（或者调用相应的样式文件）。同样的，对于屏幕设备同样可以使用“min/max”对应参数，如“min-device-width”或者“max-device-width”。

```
<link rel="stylesheet" media="screen and (max-device-width:480px)" href="iphone.css" />

```
上面的代码指的是“iphone.css”样式适用于最大设备宽度为480px，比如说iPhone上的显示，这里的“max-device-width”所指的是设备的实际分辨率，也就是指可视面积分辨率。

### 5.not关键词
使用关键词"not"是用来排除某种制定的媒体类型，也就是用来排除符合表达式的设备，换句话说，not关键词表示对后面的表达式执行取反操作，如:

```
@media not print and (max-width: 100px;){样式代码}

```
上面代码表示的是：样式代码将被使用在除打印设备和宽度小于1200px下所有设备中。

### 6.only关键词
only用来指定某种特定的媒体类型，可以用来排除不支持媒体查询的浏览器。其实only很多时候是用来对那些不支持Media Query但却支持Media Type的设备隐藏样式表的。其主要有：支持媒体特性的设备，正常调用样式，此时就当only不存在；表示不支持媒体特性但又支持媒体类型的设备，这样就会不读样式，因为其先会读取only而不是screen；另外不支持Media Queries的浏览器，不论是否支持only，样式都不会被采用。如

```
<linkrel="stylesheet" media="only screen and (max-device-width:240px)" href="android240.css" />
在Media Query中如果没有明确指定Media Type，那么其默认为all，如：

<linkrel="stylesheet" media="(min-width:701px) and (max-width:900px)" href="mediu.css" />

```
另外在样式中，还可以使用多条语句来将同一个样式应用于不同的媒体类型和媒体特性中，指定方式如下所示。

```
<linkrel="stylesheet" type="text/css" href="style.css" media="handheld and (max-width:480px), screen and (min-width:960px)" />

```
上面代码中style.css样式被用在宽度小于或等于480px的手持设备上，或者被用于屏幕宽度大于或等于960px的设备上。

到目前为止，CSS3 Media Queries得到了众多浏览器支持，除了IE6-8浏览器不支持之外，在所有现代浏览器中都可以完美支持。还有一个与众不同的时，Media Queries在其他浏览器中不要像其他CSS3属性一样在不同的浏览器中添加前缀。

### 响应式设计
什么是响应式设计呢？维基百科是这样对响应式作的描述：“Responsive设计简单的称为RWD，是精心提供各种设备都能浏览网页的一种设计方法，RWD能让你的网页在不同的设备中展现不同的设计风格。”从这一点描述来说，RWD不是流体布局，也不是网格布局，而是一种独特的网页设计方法。

响应式设计要考虑元素布局的秩序，而且还需要做到“有求必应”，那就需要满足以下三个条件：网站必须建立灵活的网格基础；引用到网站的图片必须是可伸缩的；不同的显示风格，需要在Media Queries上写不同的样式。

要想灵活的使用Responsive，仅满足这几个条件还是不够的，我们必须对Responsive有一个全面的了解。

#### 1.流体网络
流体网格是一个简单的网格系统，这种网格设计参考了流体设计中的网格系统，将每个网格格子使用百分比单位来控制网格大小。这种网格系统最大的好处是让你的网格大小随时根据屏幕尺寸大小做出相对应的比例缩放。

#### 2.弹性图片
弹性图片指的是不给图片设置固定尺寸，而是根据流体网格进行缩放，用于适应各种网格的尺寸。而实现方法是比较简单，一句代码就能搞定的事情。

img {max-width:100%;}

#### 3.媒体查询

媒体查询在CSS3中得到了强大的扩展。使用这个属性可以让你的设计根据用户终端设备适配对应的样式。这也是响应式设计中最为关键的。可以说Responsive设计离开了Medial Queries就失去了他生存的意义。简单的说媒体查询可以根据设备的尺寸，查询出适配的样式。Responsive设计最关注的就是：根据用户的使用设备的当前宽度，你的Web页面将加载一个备用的样式，实现特定的页面风格。

#### 4.屏幕分辨率
屏幕分辨简单点说就是用户显示器的分辨率，深一点说，屏幕分辨率指的是用户使用的设备浏览您的Web页面时的显示屏幕的分辨率，比如说智能手机浏览器、移动电脑浏览器、平板电脑浏览器和桌面浏览器的分辨率。Responsive设计利用Media Queries属性针对浏览器使用的分辨率来适配对应的CSS样式。因此屏幕分辨率在Responsive设计中是一个很重要的东西，因为只有知道Web页面要在哪种分辨率下显示何种效果，才能调用对应的样式。

#### 5.主要断点
主要断点，在Web开发中是一个新词，但对于Responsive设计中是一个很重要的一部分。简单的描述就是，设备宽度的临界点。在Media Queries中，其中媒体特性“min-width”和“max-width”对应的属性值就是响应式设计中的断点值。简单点说，就是使用主要断点和次要断点，创建媒体查询的条件。而每个断点会对应调用一个样式文件（或者样式代码），如下图所示：
<img alt="" src="http://img.mukewang.com/53660c230001fb9603190203.jpg" style="width: 500px;">

### Responsive 设计 meta标签

<img alt="" src="http://img.mukewang.com/53660f2c0001190005270386.jpg" style="width: 600px;">

```
<meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no/">

```

#### 自由缩放属性 resize
自由缩放属性resize
为了增强用户体验，CSS3增加了很多新的属性，其中resize就是一个重要的属性，它允许用户通过拖动的方式来修改元素的尺寸来改变元素的大小。到目前为止，可以使用overflow属性的任何容器元素。

在此之前，Web设计师为了要实现这样具有拖动效果的UI，使用大量的脚本代码才能实现，这样费时费力，效率极低。

resize属性主要是用来改变元素尺寸大小的，其主要目的是增强用户体验。但使用方法却是极其的简单，先从其语法入手。

resize: none | both | horizontal | vertical | inherit
<table border="1" cellpadding="0" cellspacing="0">
	<tbody>
		<tr>
			<td style="width:121px;">
			<p style="text-align: center;"><strong>属性值</strong></p>
			</td>
			<td style="width:447px;">
			<p style="text-align: center;"><strong>取值说明</strong></p>
			</td>
		</tr>
		<tr>
			<td style="width:121px;">
			<p style="text-align: center;">none</p>
			</td>
			<td style="width:447px;">
			<p align="left">用户不能拖动元素修改尺寸大小。</p>
			</td>
		</tr>
		<tr>
			<td style="width:121px;">
			<p style="text-align: center;">both</p>
			</td>
			<td style="width:447px;">
			<p>用户可以拖动元素，同时修改元素的宽度和高度</p>
			</td>
		</tr>
		<tr>
			<td style="width:121px;">
			<p style="text-align: center;">horizontal</p>
			</td>
			<td style="width:447px;">
			<p>用户可以拖动元素，仅可以修改元素的宽度，但不能修改元素的高度。</p>
			</td>
		</tr>
		<tr>
			<td style="width:121px;">
			<p style="text-align: center;">vertical</p>
			</td>
			<td style="width:447px;">
			<p>用户可以拖动元素，仅可以修改元素的高度，但不能修改元素的宽度。</p>
			</td>
		</tr>
		<tr>
			<td style="width:121px;">
			<p style="text-align: center;">inherit</p>
			</td>
			<td style="width:447px;">
			<p align="left">继承父元素的resize属性值。</p>
			</td>
		</tr>
	</tbody>
</table>#### CSS3外轮廓属性
外轮廓outline在页面中呈现的效果和边框border呈现的效果极其相似，但和元素边框border完全不同，外轮廓线不占用网页布局空间，不一定是矩形，外轮廓是属于一种动态样式，只有元素获取到焦点或者被激活时呈现。

outline属性早在CSS2中就出现了，主要是用来在元素周围绘制一条轮廓线，可以起到突出元素的作用。但是并未得到各主流浏览器的广泛支持，在CSS3中对outline作了一定的扩展，在以前的基础上增加新特性。outline属性的基本语法如下：

outline: ［outline-color］ || [outline-style] || [outline-width] || [outline-offset] || inherit
 outline: red solid 2px;
 
#### CSS3生成内容以及清除浮动
在Web中插入内容，在CSS2.1时代依靠的是JavaScript来实现。但进入CSS3进代之后我们可以通过CSS3的伪类“:before”，“:after”和CSS3的伪元素“::before”、“::after”来实现，其关键是依靠CSS3中的“content”属性来实现。不过这个属性对于img和input元素不起作用。

在CSS中有一种清楚浮动的方法叫"clearfix",而这个“clearfix”方法就中就使用了“content”，只不过只是在这里插入了一个空格。如下所示：

```
.clearfix:before,

.clearfix:after {

       content:””;

       display:table;

}

.clearfix:after {

       clear:both;

       overflow:hidden;

}

```