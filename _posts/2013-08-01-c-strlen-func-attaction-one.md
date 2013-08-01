---
layout: post
keywords: 技术
description: strlen的注意点
title: strlen()返回无符号型结果的注意点
categories: [C语言]
tags: [字符串,C语言,C++]
group: archive
icon: coffee
---
《C和指针》里面特意说明了strlen需要注意的返回结果的类型是无符号类型，而这个不注意则会引发后面一些离奇的错误。

“if( strlen(x) - strlen(y) >= 0 )” 和 “if( strlen(x) - 10 >= 0)”是有区别的。

理由如下图：
![Input](/image/post/c-strlen-unsigned-int-and-int.png)