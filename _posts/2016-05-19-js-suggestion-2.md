---
layout: post
title: js使用建议2
date: 2016-05-19 22:53:00 +0800
description: js使用建议2 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---
1. 谨慎使用==运算符，

```
console.log(''=='0');//==>false
console.log(0=='0');//==>true
console.log(0=='');//==>true
console.log(false=='false');//==false
console.log(false=='0');//==>true
console.log(false==undefined);//==>false
console.log(false==null);//==>false
console.log(null==undefined);//==>true
```

2. 小心逗号运算符

```
var a = (1,2,3,4);
console.log(a);
a = 1,2,3,4;
console.log(a);
```

3. 使用括号使逻辑清晰，
```
(true&&false||true);
```
尽量使用括号使其明朗
```
(true&&(false||true))
```

4. 使用块符号使语句明确

```
if(1)
    console.log(1)
    if(0)
         console.log(0)
else
     console.log(1)
    
//尽量使用
if(1){
     console.log(1)
}
if(0){
     console.log(0)
}else{
     console.log(1)
}
```

5. 提高循环效率

```
var a = [];
for(var i =0;i<500000;i++){
    a.push(Math.random())
};

console.time("for--");
var totle = 0;
for(var i =a.length;i>0;i--){
    totle+=a[i-1]
}
console.log(totle);
console.timeEnd("for--");//==>谷歌40.172ms

console.time("for++");
var totle = 0;
for(var i =0,len =a.length;i<len;i++){
    totle+=a[i]
}
console.log(totle);
console.timeEnd("for++");//==>谷歌13.791ms

console.time("for++2");
var totle = 0;
for(var i =0;i<a.length;i++){
    totle+=a[i]
}
console.log(totle);
console.timeEnd("for++2");//==>谷歌15.790ms

console.time("forEach");
var totle= 0;
a.forEach(function(value){
totle+=value
})
console.log(totle);
console.timeEnd("forEach");//==>谷歌48.497ms

```

6. if和switch比较，一般情况下两者效率差不多，相对来说switch效率更高一点，这在条件数很大时才比较明显，主要在于当条件增加时，if性能负担增加的程度更大，所以，在条件较少时，用if，当条件较多时，用switch
7. 优化if语句，将概率高的判断放在前面,进行二分法进行分条件

```
if(value==1){
    return 1;
}else if(value==2){
    return 2;
}else if(value==3){
    return 3;
}else if(value==4){
    return 4;
}else if(value==5){
    return 5;
}
else if(value==6){
    return 6;
}
//优化代码
if(value<4){
    if(value==1){
        return 1;
    }else if(value==2){
        return 2;
    }else if(value==3){
        return 3;
    }
}else{
    if(value==4){
        return 4;
    }else if(value==5){
        return 5;
    }
    else if(value==6){
        return 6;
    }
}
```


8. 减少if嵌套

```
if(a){
    if(b){
        if(c){
             if(d){
                 console.log("所有条件都成立")
            }else{
                console.log("条件d不成立")
            }
        }else{
            console.log("条件c不成立")
        }
    }else{
        console.log("条件b不成立")
    }
}else{
    console.log("条件a不成立")
}
//优化代码
var bool = true;
if(!a){
    console.log("条件a不成立");
    bool =false;
}
if(bool&&!b){
   console.log("条件b不成立");
    bool =false;
}
if(bool&&!c){
   console.log("条件c不成立");
    bool =false;
}

if(bool&&!d){
   console.log("条件d不成立");
    bool =false;
}
if(bool){
    console.log("所有条件都成立")
}
//如果你只是要判断所有条件
if(a&&b&&c&&d){
     console.log("所有条件都成立")
}

```

