---
layout: post
title: Freemarker使用shiro标签
date: 2017-02-03 00:00:00 +0800
description: Freemarker使用shiro标签 # Add post description (optional)
img:  # Add image post (optional)
tags: [java] # add tag
---

### shiro标签
- shiro.guest:游客标签，表示用户未登录时状态（包括未记住用户）
```
<@shiro.guest>    
用户未登录
</@shiro.guest> 
```
- shiro.user：用户标签，表示用户已登录时状态（包括记住的用户）
```
<@shiro.user>    
用户已登录
</@shiro.user> 
```
- shiro.authenticated：用户标签，表示用户已登录时的状态（不包括记住的用户）
```
<@shiro.authenticated>    
用户已登录
</@shiro.authenticated> 
```
- shiro.notAuthenticated：游客标签，表示用户未登录时状态（包含已记住的用户）
```
<@shiro.notAuthenticated>    
用户未登录
</@shiro.notAuthenticated> 
```
- shiro.principal：当前用户信息，一般为用户名
```
你好！<@shiro.principal/>    
```
- shiro.hasRole：验证用户是否存在某角色
```
<@shiro.hasRole name="admin">    
用户拥有amdin角色
</@shiro.hasRole> 
```
- shiro.lacksRole：验证用户是否不存在某角色
```
<@shiro.lacksRole name="admin">    
用户不拥有amdin角色
</@shiro.lacksRole> 
```
- shiro.hasAnyRole：验证用户是否存在以下任意一角色
```
<@shiro.hasAnyRole name="admin,role1,role2">    用户拥有admin，role1，role2中的任意一个角色
</@shiro.hasAnyRole> 
```
- shiro.hasPermission：验证用户是否存在某权限
```
<@shiro.hasPermission name="user:create">    
用户拥有create权限
</@shiro.hasPermission> 
```
- shiro.lacksPermission：验证用户是否不存在某权限
```
<@shiro.lacksPermission  name="user:create">
用户没有create权限
</@shiro.lacksPermission> 
```