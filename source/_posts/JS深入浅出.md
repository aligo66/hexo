---
title: JS深入浅出
date: 2017-04-28 14:40:40
tags: JS
categories: JS
---
#JS深入浅出

## 数据类型
### 原始类型
1.number     数字

2.string  	字符

3.boolean     布尔值   true or false

4.null        空 值

5.undefined   未定义

### object 对象类型
1. Function

2. Array

3. Date 

### 隐式转换
#### + 和 -

```
var x = 'The answer is '  +42;
var y = 42 + 'is the answer';

```
num 变成 数字类型  num - 0

num 变成字符串     num + "

#### == 转换数据类型

```
"123" == 123;
true
0 == false;
true
null == undefined;
true


```

#### a === b

```
类型不同，返回false
类型相同:
	null === null
	undefined === undefined
	NaN ≠ NaN
	new Object ≠ new Object
	
```

### 包装对象

```
var str = "string";
undefined
var strObj = new String("string");
undefined
str
"string"
strObj
String {0: "s", 1: "t", 2: "r", 3: "i", 4: "n", 5: "g", length: 6, [[PrimitiveValue]]: "string"}

```
