---
layout: post
title: startsWith和endsWith
date: 2018-05-07 00:00:00 +0800
description: startsWith和endsWith # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---
IE下不支持startsWith和endsWith，添加方法：
#### startsWith 
```
if (typeof String.prototype.startsWith != 'function') {
  String.prototype.startsWith = function (prefix){
    return this.slice(0, prefix.length) === prefix;
  };
}
```
#### endsWith 
```
if (typeof String.prototype.endsWith != 'function') {
  String.prototype.endsWith = function(suffix) {
    return this.indexOf(suffix, this.length - suffix.length) !== -1;
  };
}
```
