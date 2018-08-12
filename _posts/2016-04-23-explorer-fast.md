---
layout: post
title: 国产浏览器默认用极速模式渲染
date: 2016-04-23 00:00:00 +0800
description: 国产浏览器默认用极速模式渲染 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---

国内浏览器厂商一般都支持兼容模式（即 IE 内核）和高速模式（即 webkit 内核），不幸的是，所有国产浏览器都是默认使用兼容模式，这就造成由于低版本 IE （IE8 及以下）内核让基于 Bootstrap 构建的网站展现效果很糟糕的情况。幸运的是，国内浏览器厂商逐渐意识到了这一点，某些厂商已经开始有所作为了！
将下面的 <meta> 标签加入到页面中，可以让部分国产浏览器默认采用高速模式渲染页面：
```
<meta name="renderer" content="webkit">
```
目前只有360浏览器支持此 <meta> 标签。希望更多国内浏览器尽快采取行动、尽快进入高速时代！
