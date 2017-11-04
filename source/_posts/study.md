layout: ajax
title: Ajax 学习
date: 2017-04-18 17:05:46
tags: ajax
categories: Web前端
---
## Ajax 概念
ajax出现之前，都是同步的  

<img src="http://ww2.sinaimg.cn/large/006tKfTcgy1feqy8jgpo4j316u0msn1q.jpg">

<img src="http://ww4.sinaimg.cn/large/006tKfTcgy1feqy9m5xfcj316w0mwgof.jpg">

<img src="http://ww2.sinaimg.cn/large/006tKfTcgy1feqyb03inej316q0mu431.jpg">
<!-- more -->
### 基本过程
1.运用HTML和CSS来实现页面
2.运用XMLHttpRequset和Web服务器进行数据的异步交换
3.运用JavaScript操作DOM,实现动态局部刷新

### XMLHttpRequset

var request = new XMLHttpRquest();

### 概念介绍——HTTP请求
一个完整的HTTP请求过程，通常有下面7个步骤:

1.建立TCP连接

2.浏览器向服务器发送请求

3.浏览器发送请求头信息

4.服务器应答

5.服务器发送应答头信息

6.服务器向浏览器发送数据

7.服务器关闭TCP连接

一个HTTP请求一般由四部分组成:

1.HTTP请求的方法或动作，比如是GET或POST

2.正在请求的URL，总得指导请求的地址是什么吧

3.请求头，包含一些客户端环境信息，身份验证信息等

4.请求体，也就是请求正文，请求正文中可以包含客户提交的查询字符串信息，表单信息等等
<img src="http://ww2.sinaimg.cn/large/006tKfTcgy1feqypty5lgj316a0m044i.jpg">

#### get与post
**get**: 　一般用于信息获取，默认Http请求方法，查询使用URL传递参数  
　　　　   对所发送信息的数量也有限制，一般在2000个字符　　

**post**: 一般用于修改服务器上的资源
		对发送信息的数量无限制

<img src="http://ww3.sinaimg.cn/large/006tKfTcgy1feqz0ouz8bj312a0eewko.jpg">

<h4 style="text-align:center;">HTTP响应内容</h4>

<img src="http://ww1.sinaimg.cn/large/006tKfTcgy1feqz21sfqtj313i0hutbh.jpg">

<h4 style="text-align:center;">HTTP状态码</h4>
<img src="http://ww3.sinaimg.cn/large/006tKfTcgy1feqz4iidpgj312i0fg7cz.jpg">

#### XMLHttpRquest请求
**open(method,url,async)**    method请求方法 GET POST 
URL, async表示请求是同步的还是异步的，一般我们使用ajax,使用异步请求,true,默认是tue,可以不填写
**send(string)** GET 可以不填写 ，或者none

```
request.open("GET",get.php,true);
request.send();

request.open("POST","post.php",true);
request.send();

第三个有用
request.open("POST","create.php",true);
request.setRequsetHeader("Content-type","application/x-www-form-urlencoded");
request.send("name=王二狗&sex=男");

```

<h3 style="text-align:center;">XMLHttpRequset取得响应</h3>

<img src="http://ww2.sinaimg.cn/large/006tKfTcgy1feqzm1klmgj315i0ky46v.jpg">

**.readyState属性** 请求状态

**0:** 请求未初始化，open还没调用

**1:** 服务器连接已建立，open已经调用了

**2:** 请求已接收，也就是接收到头信息了

**3:** 请求处理中，也就是接收到响应主体了

**4:** 请求已完成，且响应已就绪，也就是响应完成了。

```
var request = new XMLHttpRquest();
request.open("GET","get.php",true);
request.send();
request.send();
request.onreadystatechange = function(){
	if(request.readyState===4 && request.status===200){
		//做一些事情  request.responseText
	}
}

```
<h4 style="text-align:center;">php 兼容服务器</h4>
**.PHP** 是一种创建动态交互性站点的服务器脚本语言
 
**.PHP** 能够生成动态页面内容

**.PHP** 能够创建、打开、读取、写入、删除以及关闭服务器上的文件

**.PHP** 能够接收表单数据并处理

**.PHP** 能够发送并取回cookies

**.PHP** 能够添加、删除、修改数据库中的数据

**.PHP** 能够限制用户访问某些网站的页面

**...**

#### PHP测试页面
**.PHP** 脚本以<?php开头,以?>结尾

**.PHP** 文件的默认文件扩展名是.php

**.PHP** 语句以分号结尾(;)



<h4 style="text-align:center;">JSON</h4>
**.JSON:** JavasScript对象表示法(JavaScript Object Notation)

**.JSON** 是存储和交换文本信息的语法，类似XML。它采用键值对的方式来组织，易于人们阅读和编写，同时也易于机器解析和生成

**.JSON** 是独立于语言的，也就是不管什么语言，都可以解析json,只需要按照json的规则来就行

<h5 style="text-align:center;">JSON与XML比较</h5>
**.** json的长度和xml格式比起来很短小

**.** json读写的速度更快

**.** json可以使用JavaScript内建的方法直接进行解析，转换成Javascript对象，非常方便

<h5 style="text-align:center;">JSON语法规则</h5>
**.** JSON数据的格式是：名称/值对  

名称/值对组合的名称写在前面(在双引号中)，值对写在后面(同样在双引号中)，中间用冒号隔开：比如"name":"郭靖"

**.**JSON的值可以使下面这些类型:

数字(整数或浮点数)，比如123，1.23
字符串(在双引号中)
逻辑值(tue或false)
数组(在方括号中)
对象(在花括号中)
null

```
{
	"staff":[
		{"name":"洪七","age":70},
		{"name":"郭靖","age":35},
		{"name":"黄蓉","age":30}
	]
}

```
<h5 style="text-align:center;">JSON解析</h5>
1.eval和JSON.parse
2.在代码中使用eval是很危险的!特别是用它执行第三方的JSON数据(其中可能包含恶意代码时)，尽可能使用JSON.parse()方法解析字符串本身，该方法还可以捕获JSON中的语法错误。
两种方式

```
var jsondata = '{"staff":[{"name":"洪七","age":70},{"name":"郭靖","age":35},{"name":"黄蓉","age":30}]}';
var jsonobj = eval('('+ jsondata +')');
alert(jsonobj.staff[0].name);

var jsondata = '{"staff":[{"name":"洪七","age":70},{"name":"郭靖","age":35},{"name":"黄蓉","age":30}]}';
var jsonobj = JSON.parse(jsondata);
alert(jsonobj.staff[0].name);

```

<h4 style="text-align:center;">用Jquery实现Ajax</h4>
**.Jquery.ajax([settings])**

.type: 类型，"POST"或"GET",默认为"GET"

. url: 发送请求的地址

. data : 是一个对象，连同请求发送到服务器的数据

.datatype:预期服务器返回的数据类型，如果不指定，Jquery将自动根据HTTP包MIME信息来只能判断，一般我们采用json格式，可以设置为"json"

. success: 是一个方法，请求成功后的回调函数。传入返回后的数据，以及包含成功代码的字符串

.error: 是一个方法，请求失败时调用此函数，传入XMLHttpRequest 

<h4 style="text-align:center;">跨域</h4>
<img src="http://ww1.sinaimg.cn/large/006tKfTcgy1fes0n5ocxmj31800iq0yp.jpg">

**http:// www. abc.com : 8080 / scripts/jquery.js** 
事实上HTTP和HTTPS两个协议的url看上去都可以省略端口号，但是他们访问的默认端口不同

HTTP默认访问80端口

HTTPS默认访问443端口

所以http访问https肯定是跨域

端口号是8080，如果是80，可以省略

**.**javaScript处于安全方面的考虑，不允许跨域调用其他页面的对象。什么是跨域呢，简单的理解就是因为JavaScript同源策略的限制，a.com域名下的js无法操作b.com或c.com域名下的对象

<img src="http://ww1.sinaimg.cn/large/006tKfTcgy1fes1cx2jmsj317s0hiaih.jpg" style="width:600px;">

**主域名 abc.com**

**www.abc.com**  一级域名

**bbs.abc.com**  一级域名

**beijing.bbs.abc.com** 二级域名

**haidian.beijing.bbs.abc.com** 三级域名


<h5 style="text-align:center;">处理跨域方法一： 代理</h5>
通过在同域名的的Web服务器创建一个代理:

.北京服务器(域名: www.beijing.com)

 上海服务器(域名：www.shanghai.com)
 
 .比如在北京的Web服务器的后台对上海的服务进行了代理
 
 (www.beijng.com/proxy-shanghaiservice-php)来调用上海服务器
 
 (www.shanghai.com/service.php)的服务，然后再把响应结果返回给前端，这样前端调用北京同域名的服务就和调用上海的服务效果相同了。
 
 <h5>处理跨域方法二：JSONP</h5>
 
 **.JSONP**可用于解决主流浏览器的跨域数据访问的问题
 
 在www.aaa.com页面中
 
 ```
 <script>
 function jsonp(json) {
 	alert(json["name"]);
 }
 </script>
 <script src="http://www.bbb.com/jsonp.js></script>
 
 ```
 
 在www.bbb.com页面中:
 
 jsonp({"name":"洪七","age":24});