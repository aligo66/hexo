---
title: Emmet for sublime HTML/CSS代码编写神器
date: 2016-12-19 11:24:58
tags: sublime text3
categories: 前端开发
---

<img src="https://ww1.sinaimg.cn/large/006tNbRwly1fdhuo66fnmj30hs078t8v.jpg"> 
<!-- more -->
 Emmet的简单介绍

### 一、**快速编写HTML代码**

1.初始化HTML文档需要包含一些固定的标签，比如<html>、<head>、<body>等，现在你只需要输入"!"或"html5"，然后按Tab键：可以迅速创建一个HTML结构

```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	
</body>
```
<!-- more -->

2.**轻松添加class、id、文本和属性** 连续输入元素名称的ID，Emmet会自动为你补全，比如输入p#foo会生成:

```
<p id="foo></p>

```
连续输入类和id,比如p.bar#foo,会自动生成：

```
<p class="bar" id="foo"></p>

```
下面来看看如何定义HTML元素的内容和属性。你可以通过输入h1{foo}和a[href=#],就可以自动生成如下代码

```
<h1>foo</h1>
<a href="#"></a>
```
3.**嵌套** 现在你只需要一行代码就可以实现标签的嵌套。

```
>: 子元素符号， 表示嵌套的元素 p>span  
                          <p><span></span><p>

+: 同级标签符号 h1+h2       <h1></h1>
                          <h2></h2>

^:可以使该符号的标签提升一行 p>span^p 
                        <p><span></span></p>
                        <p></p>
```

4.**分组**，你可以通过嵌套和括号来快速生成一些代码块，比如输入(.foo>h1)+(.bar>h2)会自动生成如下html代码

```
<div class="foo">
<h1></h1>
</div>
<div class="bar">
<h2></h2>
</div>

```
5.**隐式标签** 声明一个带类的标签，只需要输入div.item,就会生成

```
<div class="item"></div>

```
在过去版本中，可以省略掉div。现在如果只要输入。.item,则Emmet会根据父标签进行判定。比如在ul中输入.item,就会生成

``` 
<li class="item"></li>

```

下面是所有的隐式标签名称：

li：用于ul和ol中

tr：用于table、tbody、thead和tfoot中

td：用于tr中

option：用于select和optgroup中

6.**定义多个元素** 要定义多个元素可以使用**"*"**符号。比如，ul>li*****3可以生成如下代码

```
 <ul>
  <li></li>
  <li></li>
  <li></li>
 </ul>

```

7.**定义多个带属性的元素** 如果输入 ul>li.item$*3，将会生成如下代码：

```
<ul>
 <li class="item1"></li>
 <li class="item2"></li>
 <li class="item3"></li>
</ul>

```

### 二、css缩写

1.**值** 比如要定义元素的宽度，只需要输入W100，即可生成

```
css代码
width: 100px;

```
除了px，也可以生成其他单位，比如输入h10p+m5e,结果如下：

```
css代码
1.height: 10%;
2.margin:5em;
单位别名列表：
    p表示%
    e表示em
    x表示ex

```
2.**附加属性** 可能你之前已经了解了一些缩写，比如@f,可以生成：

```
css代码
@font-face {
font-family:;
src: url();
}

```
3.**模糊匹配** 如果有哪些缩写你拿不准，Emmet会根据你的输入内容匹配最接近的语法，比如输入ov:h、ov-h、ovh都会生成

```
css代码
overflow: hidden;

```
4.**供应商前缀** 如果输入非W3C标准的CSS属性，Emmet会自动加上供应商前缀，比如输入trs会生成

```
css代码
-webkit-transform: ;
-moz-transform: ;
-ms-transform: ;
-o-transform: ;
transform: ;

```
### 三、你还可以定制Emmet插件：

1.添加新缩写或更新现有缩写，可修改snippets.json文件

2.更改Emmet过滤器和操作的行为，可修改preferences.json文件

3.定义如何生成HTML或XML代码，可修改syntaxProfiles.json文件


