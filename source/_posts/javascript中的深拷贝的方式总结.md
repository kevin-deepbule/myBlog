---
title: javascript中的深拷贝的方式总结
date: 2021-01-01 21:26:09
tags: [javascript,前端]
categories: 前端
description: ''
password: 19981105ykw
---
## javascript中的深拷贝的方式总结
<!--more-->

# 前言

深拷贝指拷贝多层数据，每一层的数据都会被拷贝

# 一、使用递归实现深拷贝（函数不支持）

## 方法一：第一个参数是拷贝后数据的存储对象，第二个时候拷贝的对象
## 思路：
利用for in 把对象或数组中的值取出来，判断类型后赋值或递归

```javascript

 function DeepReproduce(reproduce_obj, obj) { //对对象进行复制
        if (obj && typeof obj == "object") { //传入的不能是null 和 function   
            for (var k in obj) {
                if (obj.hasOwnProperty(k)) {
                    if (typeof obj[k] == 'object'){
                        reproduce_obj[k] = Array.isArray(obj[k]) ? [] : {};//判断数组还是对
                        DeepReproduce(reproduce_obj[k], obj[k]);
                    } else{
                        reproduce_obj[k] = obj[k];
                    }
                }
            }
        }else{
        	reproduce = null;
        }
    }
```
## 测试
测试代码
```javascript
var obj = {
        id: 1,
        hobbies:["play basketball play football"],
        name: "ykw",
        age: 22,
        o: {
            id: 2,
            name: "qwq",
            o_o: {
                id: 67,
                name: "o_o"
            }
        },
        think: function(){
            console.log("think");
        }
    };
    obj.__proto__.sayHi = function () {
        console.log("nihao");
    }
    obj.__proto__.pro = "pro";
    var a = {};
    DeepReproduce(a, obj);
    console.log(a);
    console.log(a.pro);
    console.log(a.o == obj.o);
```
运行结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210131145545882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0Mzg4NDc2,size_16,color_FFFFFF,t_70)


## 方法二：return 的对象是拷贝后数据的存储对象；

```javascript
function MultiDeep(obj) {
        if (obj === null || typeof obj !== 'object') return obj;
        var reproduce_obj = obj instanceof Array ? [] : {};
        for (var k in obj) {
            if(obj.hasOwnProperty(k))
            reproduce_obj[k] = MultiDeep(obj[k]);
        }
        return reproduce_obj;
    }
```
## 测试结果
测试代码，obj 和上面一致

```javascript
 var a = MultiDeep(obj);
    console.log(a);
    console.log(a.pro);
    console.log(a.o == obj.o);
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210131150354679.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0Mzg4NDc2,size_16,color_FFFFFF,t_70)


# 二、使用JSON实现对象深拷贝
## 思路：
把对象转换成json字符串,再把json字符串转换成对象
传入的obj和前面相同

```javascript
function DeepReproduce2(obj) { //对对象进行复制
       let obj_str = JSON.stringify(obj);
       let reproduce_obj = JSON.parse(obj_str);
       return reproduce_obj;
    }
    var a = DeepReproduce2(obj);
    a.think = function(){
        console.log("athink")
    }
    console.log(a);
    a.think();
    obj.think();
```
测试结果：可以看出引用对象函数也进行了深拷贝，真是好方法。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021013115160936.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0Mzg4NDc2,size_16,color_FFFFFF,t_70)
# 三、使用$.extend实现对象深拷贝
## 思路：
jQuery.extend() 函数用于将一个或多个对象的内容合并到目标对象。
指示是否深度合并
$.extend( [deep ], target, object1 [, objectN ] )
```javascript
var a = $.extend(true,{},obj);
    a.think = function(){
        console.log("athink")
    }
    console.log(a);
    console.log(a.o==obj.o)
    a.think();
    obj.think();
```
测试结果：如下图，竟然把要复制对象的__protot__复制过来了，不太好

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210131152922381.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0Mzg4NDc2,size_16,color_FFFFFF,t_70)



# 总结
<font color=#999AAA >加快学习速度！！！！！！！！！！！！！！！！
