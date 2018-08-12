---
layout: post
title: Array的最大长度
date: 2018-08-09 00:00:00 +0800
description: Array的最大长度 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---

array的最大长度为Math.pow(2,32)-1
var arr = new Array(Math.pow(2,32));//报错Invalid array length
为什么呢，无符号int型的最大长度为2的32次方-1
为什么是2的32次方-1
整型为4个字节，一个字节8，即32位，本来第一位为符号位，无符号整型就从第一位开始计数了，所以范围为0到2的32次方-1