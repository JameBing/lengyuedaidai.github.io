---
layout: post
title: 利用filter数组去重
date: 2018-08-10 00:00:00 +0800
description: 利用filter数组去重 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---
```
Array.prototype.unique = function(){
	return this.filter(function(item,index,target){
		return index ===  target.indexOf(item)
	})
}
```
> 解析 filter并不会改变原数组，当当前值的索引等于当前值所在的第一次出现的位置相同时，则说明当前值第一次出现，若不同时，则说明它并非第一次出现



> 一般数组去重原理，定义一个新数组，依次取原数组值，如果值不存在于新数组里，则放如新数组里，最后返回新数组