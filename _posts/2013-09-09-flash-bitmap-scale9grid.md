---
layout: post
keywords: 技术
description: flash中Bitmap的Scale9Grid方法，主要介绍bytearray的ScaleBitmap类
title: flash中Bitmap的Scale9Grid方法
categories: [flash]
tags: [Bitmap,Scale9Grid,九宫格]
group: archive
icon: coffee
---
最近参加的新项目里面对资源的管理比起老项目做了一点优化，其中一点我觉得值得推崇的是swf里面的资源都是位图导出类，不再使用MoviceClip和SimpleButton。因为这两个类都释放不了里面的位图资源。

先用一个简单的Button说明
![Input](/image/post/bitmap-scale9grid-flash-labrary.png)

使用[ScaleBitmap](http://www.bytearray.org/?p=118)这个类或者参考写一个，专门处理swf里面的位图资源。这里面的有个技巧需要说明，因为设置九宫格需要传入一个Rectangle，我们可以在fla里面的创建一个MC然后设置九宫格，拉好九宫格的线，然后在动作面板键入

``` as3
trace(this.scale9Grid.x+" "+this.scale9Grid.y+" "+this.scale9Grid.width+" "+this.scale9Grid.height);
```

利用当前输出的内容构造出Rectangle传入ScaleBitmap中，bingo了。最后记得把fla里面的刚创建的MC从库中移除不要保存起来。