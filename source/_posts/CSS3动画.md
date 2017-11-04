---
title: CSS3动画
date: 2017-04-18 00:19:51
tags: CSS3
categories: CSS3
---
### CSS3变形-- 旋转rotate()
旋转rotate()函数通过指定的角度参数使元素相对原点进行旋转。它主要在二维空间内进行操作，设置一个角度值，用来指定旋转的幅度。如果这个值为正值，元素相对原点中心顺时针旋转；如果这个值为负值，元素相对原点中心逆时针旋转。

### CSS3的变形--扭曲skew()
CSS3中的变形--扭曲 skew()
扭曲skew()函数能够让元素倾斜显示。它可以将一个对象以其中心位置围绕着X轴和Y轴按照一定的角度倾斜。这与rotate()函数的旋转不同，rotate()函数只是旋转，而不会改变元素的形状。skew()函数不会旋转，而只会改变元素的形状。

Skew()具有三种情况：

1、skew(x,y)使元素在水平和垂直方向同时扭曲（X轴和Y轴同时按一定的角度值进行扭曲变形）；



第一个参数对应X轴，第二个参数对应Y轴。如果第二个参数未提供，则值为0，也就是Y轴方向上无斜切。

2、skewX(x)仅使元素在水平方向扭曲变形（X轴扭曲变形）；



3、skewY(y)仅使元素在垂直方向扭曲变形（Y轴扭曲变形）


<!-- more -->
示例演示：

通过skew（）函数将长方形变成平行四边形。

```
HTML代码：

<div class="wrapper">
  <div>我变成平形四边形</div>
</div>
CSS代码：

.wrapper {
  width: 300px;
  height: 100px;
  border: 2px dotted red;
  margin: 30px auto;
}
.wrapper div {
  width: 300px;
  height: 100px;
  line-height: 100px;
  text-align: center;
  color: #fff;
  background: orange;
  -webkit-transform: skew(45deg);
  -moz-transform:skew(45deg) 
  transform:skew(45deg);
}

```

### CSS3中的变形--缩放 scale()
缩放 scale()函数 让元素根据中心原点对对象进行缩放。

缩放 scale 具有三种情况：

1、 scale(X,Y)使元素水平方向和垂直方向同时缩放（也就是X轴和Y轴同时缩放）



例如：

div:hover {
  -webkit-transform: scale(1.5,0.5);
  -moz-transform:scale(1.5,0.5)
  transform: scale(1.5,0.5);
}
注意：Y是一个可选参数，如果没有设置Y值，则表示X，Y两个方向的缩放倍数是一样的。

2、scaleX(x)元素仅水平方向缩放（X轴缩放）



3、scaleY(y)元素仅垂直方向缩放（Y轴缩放）



HTML代码：

<div class="wrapper">
  <div>我将放大1.5倍</div>
</div>
CSS代码：

.wrapper {
  width: 200px;
  height: 200px;
  border:2px dashed red;
  margin: 100px auto;
}
.wrapper div {
  width: 200px;
  height: 200px;
  line-height: 200px;
  background: orange;
  text-align: center;
  color: #fff;
}
.wrapper div:hover {
  opacity: .5;
  -webkit-transform: scale(1.5);
  -moz-transform:scale(1.5)
  transform: scale(1.5);
}
演示结果



注意： scale()的取值默认的值为1，当值设置为0.01到0.99之间的任何值，作用使一个元素缩小；而任何大于或等于1.01的值，作用是让元素放大。

### CSS3中的变形--位移 translate()
translate()函数可以将元素向指定的方向移动，类似于position中的relative，或以简单的理解为，使用translate()函数，可以把元素从原来的位置移动，而不影响在X、Y轴的任何Web组件。
translate我们分为三种情况
1.translate(x,y)水平方向和垂直方向同时移动（也就是X轴和Y轴同时移动）
2.translateX(x)仅水平方向移动(X轴移动)
3.translateY(y)仅垂直方向移动(Y轴移动)

### CSS3的变形--矩阵 matrix()
matrix() 是一个含六个值的(a,b,c,d,e,f)变换矩阵，用来指定一个2D变换，相当于直接应用一个[a b c d e f]变换矩阵。就是基于水平方向（X轴）和垂直方向（Y轴）重新定位元素,此属性值使用涉及到数学中的矩阵，我在这里只是简单的说一下CSS3中的transform有这么一个属性值，如果需要深入了解，需要对数学矩阵有一定的知识。

```
HTML代码：

<div class="wrapper">
  <div></div>
</div>
CSS代码：
.wrapper {
  width: 300px;
  height: 200px;
  border: 2px dotted red;
  margin: 40px auto;
}
.wrapper div {
  width:300px;
  height: 200px;
  background: orange;
  -webkit-transform: matrix(1,0,0,1,50,50);
  -moz-transform:matrix(1,0,0,1,50,50);
  transform: matrix(1,0,0,1,50,50);
}

```

### CSS3中的变形--原点 transform-origin
任何一个元素都有一个中心点，默认情况之下，其中心点是居于元素X轴和Y轴的50%处。
在没有重置transform-origin改变元素原点位置的情况下，CSS变形进行的旋转、位移、缩放，扭曲等操作都是以元素自己中心位置进行变形。但很多时候，我们可以通过transform-origin来对元素进行原点位置改变，使元素原点不在元素的中心位置，以达到需要的原点位置。
### CSS3中的动画--过渡属性 transition-property
早期在Web中要实现动画效果，都是依赖于JavaScript或Flash来完成。但在CSS3中新增加了一个新的模块transition，它可以通过一些简单的CSS事件来触发元素的外观变化，让效果显得更加细腻。简单点说，就是通过鼠标的单击、获得焦点，被点击或对元素任何改变中触发，并平滑地以动画效果改变CSS的属性值。

```
在CSS中创建简单的过渡效果可以从以下几个步骤来实现
第一，在默认样式中声明元素的初始状态样式；
第二，声明过渡元素最终状态样式，比如悬浮状态；
第三，在默认样式中通过添加过渡函数，添加一些不同的样式

```
CSS3的过渡transition属性是一个复合属性，主要包括以下几个子属性。

```
transition-proerty:指定过渡或动态模拟的CSS属性

```
```
transition-duration:指定完成过渡所需的时间
```
```
trasition-timing-function:指定过渡的函数

```
```
transition-delay:指定开始出现的延迟时间
```
transition-property属性用来指定过渡动画的CSS属性名称，而这个过渡只有具备一个中值点的属性才能具备动画效果，其对应具有过渡的CSS属性主要有:
<img src="http://ww3.sinaimg.cn/large/006tKfTcly1feq3w7792gj30fb0bpdg1.jpg">

```
html:
<div></div>
css
 div {
	width:200px;
	height:200px;
	background-color: red;
	margin: 20px auto;
	-webkit-transition:background-color 0.5s ease 0.1s;
	transition:background-color 0.5s ease 0.1s;
}
div:hover {
	background-color: orange;
} 
```
### CSS3中的动画--过渡时间 transition-duration
transition-duration 属性主要用来设置一个属性过渡到另一个属性所需的时间，也就是从旧属性过渡到新属性花费的时间，俗称持续时间。
例子：
在鼠标悬停状态下，同容器从直角慢慢过渡到圆角，并让整个动画持续0.5s。

```
html代码：

<div></div>
css代码：
div {
	width: 300px;
	height: 200px;
	background-color: orange;
	margin: 20px auto;
	-webkit-transition-proerty: -wekit-border-radius;
	transition-property: border-radius;
	-webkit-transition-duration: 0.5s;
	transition-duration: 0.5s;
	-webkit-transition-timing-function: ease-out;
	-webkit-transition-delay: 0.2s;
	transition-delay: 0.2s;
}
div:hover {
	border-radius: 20px;
}

```
### CSS3的动画--过渡函数 transition-timing-function
transition-timing-function属性指的是过渡的“缓动函数”，主要用来指定浏览器的过渡速度，以及过渡期间的操作进展情况，其中要包括以下几种函数。
<img src="http://ww4.sinaimg.cn/large/006tKfTcly1feq4hxxsoxj30fo0mk77a.jpg" style="width:504px;height:530px;">

### CSS3的动画--过渡函数 transition-delay
transition-delay属性和transition-duration属性极其类似，不同的是transition-duration是用来设置过渡动画的持续时间，而transition-delay主要用来指定一个动画开始执行的时间，也就是说当改变元素属性值后多长时间开始执行。

有时我们想改变两个或者多个css属性的transition效果时，只要把几个transition的声明串在一起，用逗号（“，”）隔开，然后各自可以有各自不同的延续时间和其时间的速率变换方式。但需要值得注意的一点：第一个时间的值为 transition-duration，第二个为transition-delay。

例如：a{ transition: background 0.8s ease-in 0.3,color 0.6s ease-out 0.3;}

### CSS3 Keyframes 介绍
keyframes被称为关键帧，其类似于Flash中的关键帧。在CSS3中其主要以"@keyframes"开头，后面紧跟着是动画名称加上一对花括号"{...}",括号中就是一些不同时间段样式规则。

```
@keyframes changecolor {
	0%{
		background: red;
	}
	100% {
		background: green;
	}
}
```
在一个"@keyframes"的样式规则可以由多个百分比构成的，如在"0%"到"100%"之间创建更多个百分比，分别给每个百分比中给要有动画效果的元素加上不同的样式，从而达到一种不断变化的效果。
经验与技巧：在@keyframes中定义动画名称时，其中0%和100%还可以使用关键词from和to来代表，其中0%对应的是from,10%对应的是to

Chrome 和 Safari 需要前缀 -webkit-；Foxfire 需要前缀 -moz-。

案列演示
通过@keyframes声明一个叫"wobble"动画，从"0%"开始到"100%"结束，同时还经历了一个"40%"和"60%"的两个过程，"wobble"动画在"0%"时元素定位到left100px,背景色为green,然后在"40%"时元素过渡到left位150px,背景色为orange,然后在"60%"时元素过渡到left为150px,背景色为blue,最后"100%"时结束动画，元素又回到起点left为100px处，背景色为red

HTML:

```
<div>鼠标放到我身上</div>
```

```
css代码
@keyframes wobble {
	0% {
		margin-left: 100px;
		background: green;
	}
	40% {
		margin-left:150px;
		background:orange;
	}
	60% {
		margin-left: 75px;
		background: blue;	
	}
	100% {
		margin-left: 100px;
		background:red;
	}
}
div {
	width:100px;
	height:100px;
	background:red;
	color:#fff;
}
div {
	animation: wobble 5s ease 0.1s;
}
```
### CSS3中调用动画
animation-name属性主要是用来调用 @keyframes 定义好的动画。需要特别注意: animation-name 调用的动画名需要和“@keyframes”定义的动画名称完全一致（区分大小写），如果不一致将不具有任何动画效果。

语法：

```
animation-name: none | IDENT[,none|DENT]*;

```
1、IDENT是由 @keyframes 创建的动画名，上面已经讲过了（animation-name 调用的动画名需要和“@keyframes”定义的动画名称完全一致）；

2、none为默认值，当值为 none 时，将没有任何动画效果,这可以用于覆盖任何动画。

注意：需要在 Chrome 和 Safari 上面的基础上加上-webkit-前缀，Firefox加上-moz-。

### CSS3设置动画播放时间
animation-duration主要用来设置CSS3动画播放时间，其使用方法和transition-duration类似，是用来指定元素播放动画所持续的时间长，也就是完成从0%到100%一次动画所需时间，单位：S秒
语法规则

```
animation-duration: <time>[,<time>]*

```
取值<time>为数值，单位为秒，其默认值为“0”，这意味着动画周期为“0”，也就是没有动画效果（如果值为负值会被视为“0”）。

案列演示
制作一个矩形变成圆形的动画，整个动画持续了10秒钟

```
html
<div>Hover Me</div>
```
css:

```
@keyframes toradius{
  from {
    border-radius: 0;
  }
  to {
    border-radius: 100%;
  }
}
div {
  width: 200px;
  height: 200px;
  line-height: 200px;
  text-align: center;
  color: #fff;
  background: green;
  margin: 20px auto;
}
div:hover {
  animation-name: toradius;
  animation-duration: 10s;
  animation-timing-function: ease-in-out;
  animation-delay: .1s;
}
```
### CSS3设置动画播放方式
animation-timing-function属性主要用来设置动画播放方式主要让元素根据时间的推进来改变属性值的变换速率，简单点说就是动画的播放方式。

```
animation-timing-function:ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>) [, ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>)]*

```

### CSS3设置动画开始播放的时间
animation-delay属性用来定义动画开始播放的时间，用来触发动画播放的时间点，和transition-delay属性一样，用于定义在浏览器开始执行动画之前等待的时间。
语法规则：

```
animation-delay: <time>

```
###CSS3中设置动画播放次数
animation-iteration-count属性主要用来定义动画的播放次数。
语法规则:

```
animation-iteration-count: infinite | <number> [,infinite | <number>]*

```

1.其值通常为整数，但也可以用带有小数的数字，其默认值为1，这意味着动画将从开始到结束只播放一次。
2.如果取值为infinite,动画将会无限次的播放。
例子：
通过animation-iteration-count属性让动画move只播放5次，代码设置为

```
animation-iteration-count: 5;

```

### CSS3设置动画播放方向
animation-direction属性主要用来设置动画播放方向，其语法规则如下

```
animation-direction:normal | alternate [,normal| alternate]*

```
主要有两个值:normal、alternate
1.normal是默认值，如果设置为normal时，动画的每次循环都是向前播放。
2.第一个值alternate,它的作用是，动画播放在第偶数次向前播放，第奇数次向反方向播放。
例如：通过animation-direction属性，将move动画播放动画方向设置为alternate,代码为:

```
animation-direction: alternate;

```

### CSS3设置动画的播放状态
animation-play-state 属性主要用来控制动画的播放状态。
参数:
其主要有两个值:running和paused,
其中running是其默认值，主要作用就是类似于音乐播放器一样，可以通过paused将正在播放的动画停下来，也可以通过running将暂停的动画重新播放，这里的重新播放不一定是从元素动画的开始播放，而是从暂停的那个位置开始播放，另外如果暂停了动画的播放，元素的样式将回到最原始设置状态。
例如,页面加载时，动画不播放。代码如下:

```
animation-play-state: paused;
```

```
css代码

@keyframes move {
  0%{
    transform: translateY(90px);
  }
  15%{
    transform: translate(90px,90px);
  }
  30%{
    transform: translate(180px,90px);
  }
  45%{
    transform: translate(90px,90px);
  }
  60%{
    transform: translate(90px,0);
  }
  75%{
    transform: translate(90px,90px);
  }
  90%{
    transform: translate(90px,180px);
  }
  100%{
    transform: translate(90px,90px);
  }
}

div {
  width: 200px;
  height: 200px;
  border: 1px solid red;
  margin: 20px auto;
}
span {
  display: inline-block;
  width: 20px;
  height: 20px;
  background: orange;
  transform: translateY(90px);
  animation-name: move;
  animation-duration: 10s;
  animation-timing-function: ease-in;
  animation-delay: .2s;
  animation-iteration-count:infinite;
  animation-direction:alternate;
  animation-play-state:paused;
}
div:hover span {
  animation-play-state:running;
}

```

### CSS3多列布局-Columns
为了能在Web页面中方便实现类似报纸、杂志那种多列排版的布局，CSS3多列布局，
语法：

```
columns：<column-width> || <column-count>
```
多列布局columns属性参数主要就两个属性参数：列宽和列数。

<column-width> 主要用来定义多列中每列的宽度

<column-count> 主要用来定义多列中的列数

举例：要显示2栏显示，每栏宽度为200px，代码为：

columns: 200px 2;

#### CSS3 列间距column-gap
column-gap主要用来设置列与列之间的间距，其语法规则如下

```
column-gap: normal || <length>

```

#### CSS3 列表边框column-rule

语法规则

```
column-rule:<column-rule-width>|<column-rule-style>|<column-rule-color>

```

例如：为了能有效区分栏目列之间的关系，可以为其设置一个列边框，代码为：

column-rule: 2px dotted green;

#### CSS3 跨列设置column-span
column-span主要用来定义一个分列元素中的子元素能跨列多少。column-width、column-count等属性能让一元素分成多列，不管里面元素如何排放顺序，他们都是从左向右的放置内容，但有时我们需要基中一段内容或一个标题不进行分列，也就是横跨所有列，此时column-span就可以轻松实现，此属性的语法如下。

column-span: none | all
取值说明

属性值

属性值说明

none

此值为column-span的默认值，表示不跨越任何列。

all

这个值跟none值刚好相反，表示的是元素跨越所有列，并定位在列的Ｚ轴之上。

例如：将第一个标题跨越所有列，代码：

```
column-span:all;
```