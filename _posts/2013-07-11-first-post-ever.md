---
layout: post
keywords: 生活
description: 关于我
title: 开篇
categories: [life]
tags: [about me]
group: archive
icon: coffee
---

左折腾右折腾，终于在github这里搞上了jekyll。其实之前一直都有了解这个东西，但已经不像大学的时候那么有精力去更新blog。只是最近面试tx，其中一个环节，面试官让我把自己平时的blog和文章发给他看，我听到这词就慌了，我只有很不好意思的把自己尘封了2年之久的[百度空间](http://hi.baidu.com/free0103zhang)和自己的[github](http://github.com/zhangfree)给他看，估计是他觉得里面内容水分太多干货太少，所以就没了后文。不过正是这次tx的面试让我重新地认识到自己的不足，我也因此花了几天时间反省自己的学习方法和重新梳理了自己的知识网。


第一篇的日志我觉得除了唠叨几句，更是要总结我在弄github+jekyll的一些注意点。

关于git和github我就不费口舌了，网上资料一堆一堆的。

说到jekyll则要推荐'阮一峰的[《搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门》](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)，通过这篇文章可以从最简单的层面去认识jekyll，有个初步的认识再去拓展挖深才更加高效。

在对jekyll有一定了解之后，可以到[mojombo/jekyll](https://github.com/mojombo/jekyll/wiki/sites)找找一些自己喜欢的blog，然后check out下来自己修改，一边修改一边谷歌。我就挑了[pengx17](https://github.com/pengx17/pengx17.github.io)的，然后修改一下图标、链接和把多说改成自己的账号，这些基本就完事了。

<!-- more -->

在整个过程我就遇到一个很蛋疼的问题，我在_config.yml里面把markdown改成了rdiscount，因为网上说它比默认的Maruku要高效，后来我在localhost预览的时候没问题但上传到github之后久久不更新，我就纠结了，期间还主动找到pengx17问问解决办法，不过他也不清楚。后来我直接在_config.yml把markdown注释了，上传之后刷新就OK了。。

好了废话已经说了这么多了。
