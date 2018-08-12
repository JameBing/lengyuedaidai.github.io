---
layout: post
title: js使用建议3
date: 2016-05-26 22:53:00 +0800
description: js使用建议3 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---

1. 小心if；
```
if(a=1){//==>这是true并且进行了赋值
    console.log(a)
}
if(1==a){//建议写法
    console.log(a)
}
```

2. 优化代码：

```
switch(value){
    case 0:return result0;
    case 1:return result1;
    case 2:return result2;
    case 3:return result3;
    case 4:return result4;
    case 5:return result5;
    case 6:return result6;
}
//可以优化为
var results = [result0,result1,result2,result3,result4,result5,result6];
return results[value]
//或者
var results = {result0:result0,result1:result1,result2:result2,result3:result3,result4:result4,result5:result5,result6:result6};
return results["result"+value]
```




3. 很多时候用递归可以解决很多问题，如阶乘 

```
function factorial(n){
    if(n==1){
         return 1
    } else{
        return n*factorial(n-1)
    }
};
```

小心递归调用： 

```
function a(){
    a();
};
```

两个函数互相调用：

```
function a(){
    b()
}
function b(){
  a()
}
```

4. 合理使用缓存

```
function factorial(n){
    if(n==1){
         return 1
    } else{
        return n*factorial(n-1)
    }
};
function memfactorial(n){
    if(!memfactorial.cache){
        memfactorial.cache = {
            "0":1,
           "1":1
        };
    }
    if(!memfactorial.cache.hasOwnProperty(n)){
        memfactorial.cache[n] = n*memfactorial(n-1)
    }
    return memfactorial.cache[n]
}
console.time("no-cache")
console.log(factorial(6));
console.log(factorial(5));
console.log(factorial(4));
console.timeEnd("no-cache")//==>no-cache:1.127ms

console.time("cache")
console.log(memfactorial(6));
console.log(memfactorial(5));
console.log(memfactorial(4));
console.timeEnd("cache")//=>=cache: 0.780ms

```

5. 优化for循环。

```
var a =true;
for(var b=1;b<10;b++){
    if(a==true){
    }
}
//将if提到for循环外，避免每次for都进行判断
if(a==true){
    for(var b=1;b<10;b++){
    }
}
///////////////////////////
for(var b=1;b<10;b++){
    var a = [1,2,3,4,5,6];
    alert(a[b])
}
//将定义变量等公共部分提到for循环外面
var a = [1,2,3,4,5,6];
for(var b=1;b<10;b++){
    alert(a[b])
}
```


6. js的字符串操作

```
var a ="aa"
var b =a;
b= b.toUpperCase();
console.log(a)
console.log(b);
```

![图片](https://blog-pic-1257286366.cos.ap-chengdu.myqcloud.com/js%E5%BB%BA%E8%AE%AE/1.png)
7. 字符串拼接优化


```
console.time("=++")
var a = "" 
for(var i =0,len =1000;i<len;i++){ 
    a=a+ "aa"+"bb" 
} 
console.log(a)
console.timeEnd("=++")//==>=++: 1.743ms

console.time("+=")
var a = "" 
for(var i =0,len =1000;i<len;i++){    
        a+="aa";
        a+="bb" 
} 
console.log(a)
console.timeEnd("+=")//==>+=: 0.547ms


console.time("+=+")
var a = "" 
for(var i =0,len =1000;i<len;i++){     
    a+="aa"+"bb" 
} 
console.log(a)
console.timeEnd("+=+")//==>+=+: 0.723ms

console.time("concat")
var a = "" 
for(var i =0,len =1000;i<len;i++){ 
    a=a.concat("aa","bb")
} 
console.log(a)
console.timeEnd("concat")//==>concat: 0.877ms

console.time("join")
var a = []
for(var i =0,len =1000;i<len;i++){ 
    a.push("aa")
    a.push("bb")
} 
console.log(a.join(""))
console.timeEnd("join")//==>join: 1.164ms

```




