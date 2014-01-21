---
layout: post
keywords: 技术
description: 利用LocalConnection和ShareObject防止flash客户端多开
title: flash开发webgame中防止多开
categories: [flash]
tags: [LocalConnection,ShareObject,多开]
group: archive
icon: coffee
---
#####在flash中限制多开，可以使用LocalConnection+SharedObject
1.	SharedObject支持多个客户端SWF文件和对象之间实时数据共享。
2.	LocalConnection支持运行于同一台计算机上的在不同应用程序中的swf文件之间进行通信。

#####检测是否已经有客户端打开的基本步骤

1.	设定LocalConnection的连接名称，比如：test，用SharedObject保存一个自增字段index为0。
2.	创建LocalConnection对象，连接到名称test0。
3.	如果创建连接成功，则表示没有打开其他客户端。
4.	如果连接失败，则表示该连接已经存在，采用LocalConnection对象发送消息到该连接，设定接受消息延迟时间，同时侦听StatusEvent.STATUS事件。
5.	如果收到STATUS事件，并且evt.level == "status"，则表示已经有客户端打开了。
6.	如果连接超时，或者STATUS事件的level错误，表明连接是无效的，将SharedObject的index字段+1
7.	重复第2步，直到第3步成功。

{% highlight java %}
private var m_lcIndex:uint;
private var m_intervalID:uint;
private var m_localConnName:String;
private var m_so = SharedObject.getLocal("singleton", "/");
private var m_conn:LocalConnection = new LocalConnection();
private function checkOtherClient():void 
{
	clearTimeOut(this.m_intervalID);
	this.m_lcIndex = this.m_so.data["lc_index"] || 0;
	this.m_localConnName = "test" + this.m_lcIndex;//该名称可以定制成限制一个服务器多开
	try 
	{
		this.m_conn.client = this;
		this.m_conn.allowDomain("*");
		this.m_conn.connect(this.m_localConnName);
		//没有其他客户端存在
		//执行进入游戏逻辑
		this.enterGame();
	}
	catch (e:Error) 
	{
		this.m_conn.allowDomain("*");
		this.m_conn.send(this.m_localConnName, "clientRequired");
		this.m_conn.addEventListener(StatusEvent.STATUS, 		this.statusHandler);
		this.m_intervalID = setTimeOut(this.connectFailed, 2000);//设定超时时间为2s
	}
}
private function enterGame():void 
{
	//执行游戏逻辑
}
private function statusHandler(evt:StatusEvent):void 
{
	clearTimeOut(this.m_intervalID);
	this.m_conn.removeEventListener(evt.type, this.statusHandler);
	if (evt.level == "status") 
	{
		//检测到其他客户端
		trace("已经打开了其他客户端");
	}
	else 
	{
		this.connectFailed();
	}
}
private function connectFailed():void 
{
	clearTimeOut(this.m_intervalID);
	this.m_conn.removeEventListener(StatusEvent.STATUS, this.statusHandler);
	this.m_so.data["lc_index"] = this.m_lcIndex + 1;
	this.m_intervalID = setTimeout(this.checkOtherClient, 50);//延迟继续检测
}
public function clientRequired():void 
{
	trace("又登陆了一个客户端了。");
}
{% endhighlight %}
