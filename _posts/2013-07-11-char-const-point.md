---
layout: post
keywords: 技术
description: 指针常量与常量指针
title: const char*与char const*的区别
categories: [C/C++]
tags: [指针,C语言,C++]
group: archive
icon: coffee
---
今天晚上去一家相熟的公司面试手游客户端开发，面试官想了解我最近在研究什么技术，我只有不好意思地说在看《C和指针》这本书，刚好看到数组这一章。哎呀呀，没想到他居然问我const char*和char const*的区别，还好我有印象，但后来他又问了一下const char* const，这下我就懵了。。偶不会。

####const char*
常量指针，就是这个指针指向的数据类型必须是一个常量，但这个指针的值是可以改变的，只要指向的是常量则可。

####char const*
指针常量，就是这个指针指向的内容是char类型，且这个地址是不变的。但这个指针指向的内容是可以改变的。

####cosnt char* const
指向常量的指针常量，就是这个指针是指向常量且地址不可改变。