---
layout: post
title: CSS居中
date: 2018-03-15 00:00:00 +0800
description: CSS居中 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---

# 水平居中
对于行内元素(inline)：text-align: center;
对于块级元素(block)：设置宽度且 marigin-left 和 margin-right 是设成 auto
对于多个块级元素：对父元素设置 text-align: center;，对子元素设置 display: inline-block;；或者使用 flex 布局
# 垂直居中
对于行内元素(inline)
单行：设置上下 pandding 相等；或者设置 line-height 和 height 相等
多行：设置上下 pandding 相等；或者设置 display: table-cell; 和 vertical-align: middle;；或者使用 flex 布局；或者使用伪元素
对于块级元素(block)：下面前两种方案，父元素需使用相对布局
已知高度：子元素使用绝对布局 top: 50%;，再用负的 margin-top 把子元素往上拉一半的高度
未知高度：子元素使用绝对布局 position: absolute; top: 50%; transform: translateY(-50%);
使用 Flexbox：选择方向，justify-content: center;
# 水平垂直居中
定高定宽：先用绝对布局 top: 50%; left: 50%;，再用和宽高的一半相等的负 margin 把子元素回拉
高度和宽度未知：先用绝对布局 top: 50%; left: 50%;，再设置 transform: translate(-50%, -50%);
使用 Flexbox：justify-content: center; align-items: center;
