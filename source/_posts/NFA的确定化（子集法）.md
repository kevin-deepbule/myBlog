---
title: NFA的确定化
date: 2020-03-12 20:47:47
tags: [C,编译原理]
copyright: true
categories: 编译原理
related_posts: true
---
## NFA的确定化（子集法）
<!--more-->
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200417150016943.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0Mzg4NDc2,size_16,color_FFFFFF,t_70)如上图所示，实现一个词法分析器首先由其正规集写出他所对应的正规式，再由正规式转化为NFA；这一些部分是利于人去实现的；然后通过算法将这个NFA转化为DFA；在将DFA输入到上面的通用控制中，实现词法分析；LETex是按照这种思想实现的；
我们在这里只实现NFA的确定化；

