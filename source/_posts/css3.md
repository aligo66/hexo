---
title: css3 基础
date: 2017-04-17 16:18:06
tags: css3
categories: css3
---
## box-shadow
阴影类型：此参数可选。如不设值，默认投影方式是外阴影；如取其唯一值“inset”，其投影为内阴影；

X-offset:阴影水平偏移量，其值可以是正负值。如果值为正值，则阴影在对象的右边，其值为负值时，阴影在对象的左边；

Y-offset:阴影垂直偏移量，其值也可以是正负值。如果为正值，阴影在对象的底部，其值为负值时，阴影在对象的顶部；

阴影模糊半径：此参数可选，，但其值只能是为正值，如果其值为0时，表示阴影不具有模糊效果，其值越大阴影的边缘就越模糊；

阴影扩展半径：此参数可选，其值可以是正负值，如果值为正，则整个阴影都延展扩大，反之值为负值时，则缩小；

阴影颜色：此参数可选。如不设定颜色，浏览器会取默认色，但各浏览器默认取色不一致，特别是在webkit内核下的safari和chrome浏览器下表现为透明色，在Firefox/Opera下表现为黑色（已验证），建议不要省略此参数。
## CSS3 线性渐变
```
linegar-gradient (to bottom,#fff,#999);

```
<!--more -->
## CSS3 text-shadow

text-overflow 用来设置是否使用一个省略标记(...)标示对象内文本的溢出。
text-overflow:clip 标示剪切 | ellipsis 标示省略

但是text-overflow只是用来说明文字溢出时用什么方式显示，要实现溢出时产生省略号的效果，还须定义强制文本在一行内显示(white-space:nowrap)及溢出内容为隐藏(overflow:hidden)，只有这样才能实现溢出文本显示省略号的效果，代码如下

```
text-overflow:ellipsis;
overflow:hidden;
white-space:nowrap;​

```
同时word-wrap也可以用来设置文本行为，当前行超过指定容器的边界时是否断开转行。
语法:

```
world-wrap:normal表示控制连续文本换行 | break-word 表示内容将在边界内换行

```
## CSS3文字与字体 嵌入字体font-face
@font-face能够加载服务器端的字体文件，让浏览器可以显示用户电脑里没有安装的字体

```
@font-face {
	font-family: 字体名称;
	src : 字体文件在服务器上的相对或绝对路径
}
```
比如

```
p{
	font-face : 12px;
	font-family: "My Font";
	/*必须项，设置@font-face中font-family同样的值*/
}
```

## CSS3 文字与字体 文本阴影text-shadow
text-shadow 可以用来设置文本的阴影效果

语法：

```
text-shadow: X-Offset Y-offset blur color;
```
X-offset：表示阴影的水平偏移距离
Y-offset: 表示阴影的垂直偏移距离
Blur: 是指阴影的模糊程度，其值不能是负值，如果值越大，阴影越模糊，反之阴影越清晰，如果不需要阴影模糊可以将Blur值设置为0;
color: 是指阴影的颜色，其可以使用 rgba色，
比如，我们可以用下面代码设置阴影效果。
text-shadow: 0 1px 1px #fff;

## css3背景 background-origin
设置元素背景图片的原始起始位置。
语法：

```
background-origin : border-box | padding-box | content-box;

```
参数分别表示背景图片是从边框还是内边框(默认值)，或者是内容区域开始显示。
#### **css3背景 background-clip 图片剪切**
### css3背景 background-size

设置背景图片的大小，以长度值或百分比显示，还可以通过cover和contain来对图片进行伸缩
语法：

```
background-size: auto |<长度值> |<百分比>|cover | contain

```
1.auto: 默认值，不改变背景图片的原始高度和宽度
2. <长度值> : 成对出现如200px 50px 将背景图片宽高依次设置为前面两个值，当设置一个值时，将其作为图片宽度值来等比缩放；
3. <百分比> 0%~100%之间的任何值，将背景图片一次设置为所在元素宽高乘以前面百分比得出的数值，当设置一个值时，同上，
4. cover：覆盖，即将背景图片等比缩放至某一变紧贴容易边缘为止
5. contain: 容纳，即将背景图片等比缩放某一边，紧贴容器边缘为止。
#### css3多重背景

```
background:url(http://static.mukewang.com/static/img/logo_index.png) no-repeat
    0 0 / 75% 55%, url(http://static.mukewang.com/static/img/logo_index.png) no-repeat right bottom / 50% 40%;
```
## css3实现立体导航栏

效果
<img src="http://ww3.sinaimg.cn/large/006tKfTcgy1feptmkwaqsj313o07g75c.jpg">
代码：

```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>导航栏</title>
<style type="text/css">
	body {
		background: #ebebeb;
	}
	.nav {
		width: 560px;
		height: 50px;
		line-height: 50px;
		font-weight: bold;
		margin: 40px auto 0;
		font-family: Arial;
		background: #f65f57;
		border-radius: 5px;
		box-shadow: 0 3px 5px #666;
	}
	.nav li {
		position: relative;
		display: inline-block;
		list-style: none;
		font-size: 13px;
		text-shadow: 1px 2px 4px rgba(0,0,0,0.5);
		list-style: none outside none;
		padding: 0 16px;
	}
	.nav a {
		display: inline-block;
		-webkit-transition: all 0.2s ease-in;
		-moz-transition: all 0.2s ease-in;
		-o-transition: all 0.2s ease-in;
		-ms-transition: all 0.2s ease-in;
		transition: all 0.2s ease-in;
	}
	.nav a:hover {
		-webkit-transform:rotate(20deg);
		-ms-transform:rotate(20deg);
		-o-transform:rotate(20deg);
		-moz-transform:rotate(20deg);
		transform:rotate(20deg);
	}
/* 使用伪元素制作导航列表分割线*/
	.nav li:before {
		content: "";
		color: #666;
		position: absolute;
		height: 20px;
		width: 1px;
		top: 15px;
		left: -1px;
		background-image: linear-gradient(to right, #f65f57,#993333,#f65f57);
	}
/*删除第一项和最后一项当行分割线*/
 .nav li:first-child::before {
	background-image: none;
 }
.nav a, .nav a:hover {
	color: #fff;
	text-decoration: none;
}
</style>
</head>
<body>
	<ul class="nav">
		<li><a href="">Home</a></li>
		<li><a href="">About Me</a></li>
		<li><a href="">Protfolio</a></li>
		<li><a href="">Blog</a></li>
		<li><a href="">Resources</a></li>
		<li><a href="">Contact Me</a></li>
	</ul>
</body>
</html>
```
## CSS3选择器 属性选择器
在HTML中，通过各种各样的属性可以给元素增加很多附加的信息。例如，通过，ID属性可以将不同div元素进行区分。
实例展示

```
html代码:

<a href="xxx.pdf">我链接的是PDF文件</a>
<a href="#" class="icon">我类名是icon</a>
<a href="#“ title=”我的title是more“>我的title是more</a>

css代码
a[class^=icon] {
	background: green;
	color:#fff;
}
a[href$=pdf] {
	background: orange;
	color:#fff;
}
a[title*=more] {
	background: blue;
	color: #fff;
}

```
### CSS3结构伪类选择器 - not
div:not([id="footer"]){
  background-color: orange;
}
### CSS3 结构性伪类选择器—nth-child(n)
“:nth-child(n)”选择器用来定位某个父元素的一个或多个特定的子元素。其中“n”是其参数，而且可以是整数值(1,2,3,4)，也可以是表达式(2n+1、-n+5)和关键词(odd、even)，但参数n的起始值始终是1，而不是0。也就是说，参数n的值为0时，选择器将选择不到任何匹配的元素。
### CSS3 结构性伪类选择器—nth-last-child(n)
“:nth-last-child(n)”选择器和前面的“:nth-child(n)”选择器非常的相似，只是这里多了一个“last”，所起的作用和“:nth-child(n)”选择器有所区别，从某父元素的最后一个子元素开始计算，来选择特定的元素。
### CSS3 first-of-type选择器
“:first-of-type”选择器类似于“:first-child”选择器，不同之处就是指定了元素的类型,其主要用来定位一个父元素下的某个类型的第一个子元素。
### CSS3 nth-of-type(n)选择器
“:nth-of-type(n)”选择器和“:nth-child(n)”选择器非常类似，不同的是它只计算父元素中指定的某种类型的子元素。当某个元素中的子元素不单单是同一种类型的子元素时，使用“:nth-of-type(n)”选择器来定位于父元素中某种类型的子元素是非常方便和有用的。在“:nth-of-type(n)”选择器中的“n”和“:nth-child(n)”选择器中的“n”参数也一样，可以是具体的整数，也可以是表达式，还可以是关键词。
### CSS3 only-child选择器
“:only-child”选择器选择的是父元素中只有一个子元素，而且只有唯一的一个子元素。也就是说，匹配的元素的父元素中仅有一个子元素，而且是一个唯一的子元素。
### CSS3 only-of-type选择器
“:only-of-type”选择器用来选择一个元素是它的父元素的唯一一个相同类型的子元素。这样说或许不太好理解，换一种说法。“:only-of-type”是表示一个元素他有很多个子元素，而其中只有一种类型的子元素是唯一的，使用“:only-of-type”选择器就可以选中这个元素中的唯一一个类型子元素。

### CSS3选择器下
#### CSS3选择器 :enabled选择器
在Web的表单中，有些表单元素有可用（“:enabled”）和不可用（“:disabled”）状态，比如输入框，密码框，复选框等。在默认情况之下，这些表单元素都处在可用状态。那么我们可以通过伪选择器“:enabled”对这些表单元素设置样式。

示例演示

通过“:enabled”选择器，修改文本输入框的边框为2像素的红色边框，并设置它的背景为灰色。

#### ::selection
CSS3选择器 ::selection选择器
“::selection”伪元素是用来匹配突出显示的文本(用鼠标选择文本时的文本)。浏览器默认情况下，用鼠标选择网页文本是以“深蓝的背景，白色的字体”显示的，效果如下图所示：



从上图中可以看出，用鼠标选中“专注IT、互联网技术”、“纯干货、学以致用”、“没错、这是免费的”这三行文本中，默认显示样式为：蓝色背景、白色文本。

有的时候设计要求,不使用上图那种浏览器默认的突出文本效果，需要一个与众不同的效果，此时“::selection”伪元素就非常的实用。不过在Firefox浏览器还需要添加前缀。
#### CSS3选择器 :read-only选择器
“:read-only”伪类选择器用来指定处于只读状态元素的样式。简单点理解就是，元素中设置了“readonly=’readonly’”

#### CSS3选择器 :read-write选择器
“:read-write”选择器刚好与“:read-only”选择器相反，主要用来指定当元素处于非只读状态时的样式。

### css3选择器 ::before 和 ::after
:before和::after这两个主要用来给元素的前面或后面插入内容，这两个常和"content"配合使用，使用的场景最多的就是清除浮动。

```
.clearfix::before,
.clearfix::after {
    content: ".";
    display: block;
    height: 0;
    visibility: hidden;
}
.clearfix:after {clear: both;}
.clearfix {zoom: 1;}
```