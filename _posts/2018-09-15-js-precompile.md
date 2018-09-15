---
layout: post
title: js函数预编译过程
date: 2018-09-15 00:00:00 +0800
description: js函数预编译过程 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---
1. 创建函数执行上下文
2. 声明形参
3. 变量提升
4. 挂接实参
5. 函数提升
6. 然后按照预编译后结果依次执行

举个栗子

```
function demo(a,b,c,d,e){
	console.info("a:"+a);
	console.info("b:"+b);
	console.info("c:"+c);
	console.info("d:"+d);
	console.info("e:"+e);
	console.info("f:"+f);
	var a = 1;
	var b = function(){};
	var c = 3
	function c(){};
	var d = 4;
	f = 6;
	console.info("a:"+a);
	console.info("b:"+b);
	console.info("c:"+c);
	console.info("d:"+d);
	console.info("e:"+e);
	console.info("f:"+f);
	var f;
}
demo("a","b","c","d","e")
```
输出结果：

```
a:a
b:b
c:function c(){}
d:d
e:e
f:undefined
a:1
b:function(){}
c:3
d:4
e:e
f:6
```
