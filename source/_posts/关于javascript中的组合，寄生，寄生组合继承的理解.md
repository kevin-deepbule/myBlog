---
title: 关于javascript中的组合，寄生，寄生组合继承的理解
related_posts: true
copyright: true
date: 2021-02-02 20:37:05
tags: [javascript,前端]
categories: javascript
---
## javascript中的组合，寄生，寄生组合继承
<!--more-->
# 目录
## 什么是继承

 继承是让子类获得父类的属性和方法，或者可以重新定义属性和方法

## 寄生式继承
如何实现继承呢？
在ES6前并没有类，没有关键字extends 如何实现呢？
从继承的结果来看，继承就是让子对象拥有父对象的属性和方法。我们很容易就能想到，我们将父对象直接赋值给子对象，这样子对象便有了父对象的全部属性和方法。这么浅显的道理便是寄生式继承。当然可以对子对象进行增强（也就是重写方法或增加属性)
//寄生式继承实例

```javascript
var father = {
        name: "father",
        age : 34
    }
    father.__proto__.talk = function(){
            console.log(this.name);
        }
    function Son(superType){    //寄生式继承函数实际上是复制一份父类对象，给这个父类对象添加属性
        var subType = Object(father);//将实例对象完全复制一份 给subType
        subType.name = "son";//重新赋值
        return subType;
    }
    var son = Son(father)
    console.log(son)
```
从这个寄生式继承我们可看到，我们仅仅是将一个父对象复制了一份赋值给子对象，很明显，这一种方法有很大的弊端，子对象虽然有了和父亲一样的属性和方法，但是属性值和一样，需要重新赋值，这好吗？这不好。这个方法有优点吗?有，他们的原型对象是同一个。
再来看看组合式继承
## 组合式继承
因为我们继承的定义是让子类获得父类的属性和方法，所以我们理所应当的从子类的构造函数入手，看如何能让他获得父类的属性与方法。
对于属性：可以想到，在子类的构造函数中调用父类的构造函数，目的在new子类构造函数的时候，能执行父类构造函数中的代码，但是直接调用Father(参数)的话，其中的this指向的是函数的调用者，也就是window，我们是要让子类有父类的属性，不是给window添加的，所以这里在调用的时候需要用call方法指定是调用者（new的子类对象)，给子类对象添加属性。
对于方法：可以想到，通过原型链来查找，什么意思呢？就是说，给这个子类对象的原型对象等于父类对象，作用就是子类对象在查找父类对象的函数时，先在自己的属性中找，没找见，去原型对象中找，原型对象中的原型对象中找见了，于是，子类拥有了父类的方法。这便是方法的继承。（感觉很蠢，明明我们只要子类原型对象中找到父类原型对象中定义的函数，但却new了一个父类对象出来赋值给了子类的原型对象，能不能直接把父类的原型对象赋值给子类原型对象，这就是寄生组合式继承）

```javascript
function Father(name,age){
    this.name = name;
    this.age = age;
    Father.prototype.talk = function(){
    console.log(this.name);
	}
}

function Son(name,age,score){
    Father.call(this,name,age);//使当前的Father构造函数中的this是Son构造函数的实例；给该实例复值
    this.score = score;
    Son.prototype =new Father();
    Son.prototype.constructor = Son;
}

var son = new Son("son",12,99);
son.talk()
console.log(son);
```
注意：在使用组合式继承时，不能使用这种保险的方式生成构造函数，理由不必赘述，上面已经说明。

```javascript
 if (!(this instanceof Father)){
            return new Father(name,age);
        }
```

## 寄生组合式继承

```javascript
function Father(name,age){
    this.name = name;
    this.age = age;
    Father.prototype.talk = function(){
    console.log(this.name);
	}
}

function Son(name,age,score){
    Father.call(this,name,age);//使当前的Father构造函数中的this是Son构造函数的实例；给该实例复值
    this.score = score;
    Son.prototype =Father.prototype;//直接把父类的原型赋值给子类
    Son.prototype.constructor = Son;
}

var son = new Son("son",12,99);
son.talk()
console.log(son);
```


## 总结

组合式继承：指的是将原型链和借用构造函数的技术组合到一块，从而发挥二者之长的一种继承模式。其背后的思路是使用原型链实现对原型属性和方法的继承，而通过借用构造函数来实现对实例属性的继承。
寄生式继承，可以在不必预先定义构造函数的情况下实现继承，其本质是执行对给定对象的浅复制。而复制得到的副本还可以得到进一步改造
寄生组合式继承，集寄生式继承和组合继承的优点与一身，是实现基于类型继承的最有效方式。

