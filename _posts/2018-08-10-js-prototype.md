---
layout: post
title: JS原型链
date: 2018-08-10 00:00:00 +0800
description: JS原型链 # Add post description (optional)
img:  # Add image post (optional)
tags: [other] # add tag
---
js原型链就是js实现继承的一种方式体现
学过java应该都知道类的继承，继承的好处就是可以提炼公共的方法，使得代码简洁，易于维护，js也是面对对象的，但js的面对对象并非用class和继承，而是使用原型链的方式，即每个函数都存在一个prototype属性，而这个属性又指向一个对象，而这个对象就相当于父类对象，举个栗子：
```
var Bird = function(){//定义鸟这个类
this.name = "bird";//名字叫鸟
 this.power = "fly"//能力会飞
}
var Sparrow = function(){//定义麻雀对象
this.name = "sparrow"//名字叫麻雀
}
Sparrow.prototype = new Bird();//让麻雀继承鸟类的属性
var sparrowObj = new Sparrow();//创建一个麻雀对象
console.log(sparrowObj.name);//==>sparrow
console.log(sparrowObj.power);//==>fly
```
可以看出，麻雀在继承了鸟类后，拥有了飞行能力，可以很好的访问到power属性，但是name属性会已自己的内部属性为准，但是原型链中的父类属性name是否会完全覆盖呢？继续撸代码：
```
console.log(sparrowObj.__proto__.name)//==>bird
console.log(sparrowObj.name)//==>sparrow
delete sparrowObj.name;
console.log(sparrowObj.name)//==>bird
```
原来在sparrowObj 对象里面存在一个属性__proto__，它指向的就是其原型链，即其父类对象，而父类对象也有__proto_指向的是Object，而Object会指向null，如同链条一样，是不是和java又很像，一切对象最终都会继承于Object
![图片](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/js%E5%BB%BA%E8%AE%AE/prototype.png)
判断一个对象对应的构造类，isPrototypeOf或者instanceof,两者区别在于一个是正向判断，一个是逆向判断，
```
console.log(Sparrow .prototype.isPrototypeOf(sparrowObj))//==>true
console.log(Bird.prototype.isPrototypeOf(sparrowObj))//==>true
console.log(sparrowObj instanceof Sparrow)//==>true
console.log(sparrowObj instanceof Bird)//==>true
```
那如果想判断sparrowObj 的直属构造器怎么判断呢
```
console.log(sparrowObj.__proto__===Sparrow.prototype)//==>true
console.log(sparrowObj.__proto__===Bird.prototype)//==>false
```
