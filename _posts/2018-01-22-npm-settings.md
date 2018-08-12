---
layout: post
title: npm设置
date: 2018-08-09 00:00:00 +0800
description: npm设置 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---
# 设置npm代理

```
npm config set proxy http://username:password@server:port
npm config set https-proxy http://username:pawword@server:port
```

# 设置淘宝镜像

装不上时先设置
```
npm config set registry https://registry.npm.taobao.org 
```
安装cnpm
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
## 使用cnpm
安装模块
```
cnpm install [name]
```
更新模块
```
cnpm update [name]
```
设置代理
```
cnpm config set proxy http://username:password@server:port
cnpm config set https-proxy http://username:pawword@server:port
```
