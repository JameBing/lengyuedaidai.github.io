---
layout: post
title: github发布博客
date: 2018-08-10 00:00:00 +0800
description: github发布博客 # Add post description (optional)
img:  # Add image post (optional)
tags: [other] # add tag
---

1. 创建github项目：
![[图片]](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/github%E5%8F%91%E5%B8%83%E5%8D%9A%E5%AE%A2/1.png)
名字为：{{你的帐号}}.github.io
2. clone项目，创建并提交推送一个index页面
如：

```
<!DOCTYPE html>
<html>
<body>
<h1>Hello World</h1>
</body>
</html>
```

3. 打开https://{{你的帐号}}.github.io/，可以开到你刚才的页面
![[图片]](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/github%E5%8F%91%E5%B8%83%E5%8D%9A%E5%AE%A2/2.png)
这就已经算成功一半了
4. 去ruby网站下载安装ruby，[https://rubyinstaller.org/downloads/](https://rubyinstaller.org/downloads/)

5. 安装后查看是否安装成功

```
ruby -v
```


```
gem -v
```

![[图片]](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/github%E5%8F%91%E5%B8%83%E5%8D%9A%E5%AE%A2/3.png)
6. 安装jekyll

```
gem install jekyll
```

7. 查看是否安装成功

```
jekyll --version
```

![[图片]](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/github%E5%8F%91%E5%B8%83%E5%8D%9A%E5%AE%A2/4.png)
8. 创建项目
```
jekyll new blog
```

![[图片]](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/github%E5%8F%91%E5%B8%83%E5%8D%9A%E5%AE%A2/5.png)

![[图片]](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/github%E5%8F%91%E5%B8%83%E5%8D%9A%E5%AE%A2/6.png)
9. 安装bundler ，我的没安装会出现报错，一些问题可参考[https://blog.csdn.net/wudalang_gd/article/details/74619791](https://blog.csdn.net/wudalang_gd/article/details/74619791)

```
gem install bundler -r --source http://rubygems.org/
```

在你刚建的博客目录下：
```
bundle install
```

10. 启动

```
jekyll serve
```

![[图片]](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/github%E5%8F%91%E5%B8%83%E5%8D%9A%E5%AE%A2/7.png)

![[图片]](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/github%E5%8F%91%E5%B8%83%E5%8D%9A%E5%AE%A2/8.png)
11. 下载自己喜欢的模版[http://jekyllthemes.org/](http://jekyllthemes.org)

如果喜欢我的模版也可以clone我的：[https://github.com/lengyuedaidai/lengyuedaidai.github.io](https://github.com/lengyuedaidai/lengyuedaidai.github.io)