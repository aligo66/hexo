---
title: Datepicker 日历组件开发
date: 2017-04-19 22:46:01
tags: JS
categories: 前端开发
---
##### 效果如下：

<img src="http://ww3.sinaimg.cn/large/006tKfTcly1fesdlxla65j30eu0fyjs7.jpg">

<!-- more -->
HTML代码

```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>datapicker</title>
<link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
	<div class="ui-datepicker-wrapper">
		<div class="ui-datepicker-header">
			<a href="#" class="ui-datepicker-btn ui-datepicker-prev-btn">&lt;</a>
			<a href="#" class="ui-datepicker-btn ui-datepicker-next-btn">&gt;</a>
			<span class="ui-datepicker-curr-month">2017-4</span>
		</div>
		<div class="ul-datepicker-body">
			<table>
				<thead>
					<tr>
						<th>一</th>
						<th>二</th>
						<th>三</th>
						<th>四</th>
						<th>五</th>
						<th>六</th>
						<th>日</th>
					</tr>
				</thead>
				<tbody>
					<tr>
						<td>29</td>
						<td>30</td>
						<td>1</td>
						<td>2</td>
						<td>3</td>
						<td>4</td>
						<td>5</td>
					</tr>
					<tr>
						<td>6</td>
						<td>7</td>
						<td>8</td>
						<td>9</td>
						<td>10</td>
						<td>11</td>
						<td>12</td>
					</tr>
					<tr>
						<td>13</td>
						<td>14</td>
						<td>15</td>
						<td>16</td>
						<td>17</td>
						<td>18</td>
						<td>19</td>
					</tr>
					<tr>
						<td>20</td>
						<td>21</td>
						<td>22</td>
						<td>23</td>
						<td>24</td>
						<td>25</td>
						<td>26</td>
					</tr>
					<tr>
						<td>27</td>
						<td>28</td>
						<td>29</td>
						<td>30</td>
						<td>1</td>
						<td>2</td>
						<td>3</td>
					</tr>
				</tbody>
			</table>
		</div>
	</div>
</body>
</html>

```

CSS代码：

```
.ui-datepicker-wrapper {
	width: 240px;
	font-size: 16px;
	color: #666;
	-webkit-box-shadow: 2px 2px 8px 2px rgba(128,128,128,.3);
	box-shadow:  2px 2px 8px 2px rgba(128,128,128,.3);
	margin: 20px auto 0;

}
.ui-datepicker-wrapper .ui-datepicker-header {
	padding: 0 20px;
	height: 50px;
	line-height: 50px;
	text-align: center;
	background: #f0f0f0;
	border-bottom: 1px solid #ccc;
	font-weight: bold;
}
.ui-datepicker-wrapper .ui-datepicker-btn {
	font-family: serif;
	font-size: 20px;
	width: 20px;
	height: 50px;
	line-height: 50px;
	text-align: center;
	color: #1abc9c;
	cursor: pointer;
	text-decoration: none;
}
.ui-datepicker-wrapper .ui-datepicker-prev-btn {
	float: left;
}
.ui-datepicker-wrapper .ui-datepicker-next-btn {
	float: right;
}
.ui-datepicker-wrapper .ul-datepicker-body table {
	width: 100%;
	border-collapse: collapse;
}
.ui-datepicker-wrapper .ul-datepicker-body th,
.ui-datepicker-wrapper .ul-datepicker-body td {
	height: 30px;
	text-align: center;
}
.ui-datepicker-wrapper .ul-datepicker-body th {
	font-size: 12px;
	line-height: 40px;
	height: 40px;
}
.ui-datepicker-wrapper .ul-datepicker-body td {
	font-size: 10px;
	border: 1px solid #f0f0f0;
	cursor: pointer;
}

```
### 最主要的是数据部分
**数据的作用**

   渲染当月日历表格
   用于点击时取日期值
   
**日期对象**
.new Date(year,month-1,date)

.月份需要减一  传入数据的话

.越界自动进(退)位

.getFullYear() 获取年份/ 

getMonth() 获取的值要比实际小1，比如当前4月，获取的是3，所以要加1/ 

.getDate() 获取多少号

.getDay() 获取星期几

. 当月第一天 new Date(year, month-1, 1);

. 当月最后一天 new Date(year, month, 0); ***代表最后一天，会倒回到31号，或者28号 30号***

.星期一到星期天 [1,2,3,4,5,6,0]
