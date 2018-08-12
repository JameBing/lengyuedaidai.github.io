---
layout: post
title: ES6语法糖
date: 2017-10-27 00:00:00 +0800
description: ES6语法糖 # Add post description (optional)
img:  # Add image post (optional)
tags: [javascript] # add tag
---


```
var events = { listeners, listen }
```
> 等同
```
var events = {
  listeners: listeners,
  listen: listen
}
```

---

```
var expertise = "name"
var person = {
    b:1
}
person[expertise] = "aa"
```
> 等同
```
var expertise = 'name'
var person = {
  b:1,
  [expertise]:"aa"
}
```

---

```
var emitter = {
  events: {},
  on: function (type, fn) {
  }
}
```
> 等同
```
var emitter = {
  events: {},
  on(type, fn) {
  }
}
```
---
```
var example = function (parameters) {
  // function body
}
```
> 等同
```
var example = (parameters) => {
  // function body
}
```
> 当只有一个参数时,等同
```
var example = parameters => {
  return parameters * 2
}
```
> 直接return时,等同
```
var example = 
parameters => parameters * 2
```
---
```
var pseudonym = character.pseudonym
```
> 等同
```
var { pseudonym } = character
```
---
```
var alias = character.pseudonym
```
> 等同
```
var { pseudonym: alias } = character
```
---
```
var gender = character.metadata.gender
```
> 等同
```
var { metadata: { gender } } = character
```
---
```
var names = ['James', 'L.']
var [ firstName = 'John', , lastName = 'Doe' ] = names
```
> 等同
```
var names = ['James', 'L.'];
var firstName = names[0]||'John';
var lastName = names[2]||'Doe';
```
---
```
var left = 5, right = 7;
var aux = left
left = right
right = aux
```
> 等同
```
var left = 5, right = 7;
[left, right] = [right, left]
```
---
```
function join() {
  var list = Array.prototype.slice.call(arguments)
  return list.join(', ')
}
join('first', 'second', 'third')
```
> 等同
```
function join(...list) {
  return list.join(', ')
}
join('first', 'second', 'third')
```