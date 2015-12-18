title: "Ajax"
date: 2015-04-13 08:08:14
tags: 语言
categories: 学习
---
###课程一(妙味课堂)
####一、Ajax简介：
--Ajax是 Asny chronous JavaScript and XML的缩写（异步JavaScript和XML）
--Ajax是把多种技术进行重新融合
--早在1996年就有Ajax了（一开始没有广泛的应用 直到后面谷歌公司的谷歌地图出现）
--Ajax可以在无需刷新整个页面的情况下实现数据在浏览器和服务器之间的传送，只改变页面的一部分。
--Ajax只能从服务器上读取文件
--Ajax读取的文件都是以文本的形式存在的
--Ajax可以给客户端返回三种格式数据(文本格式，XML，json格式)
解决办法：eval(str); eval的作用是计算字符串里的内容（他能计算所有的Js代码）

--Ajax作用仅能从服务器上读取文件 但它的应用有很多

#####Ajax原理
1、http请求方法： 
(1)GET方法   (他是把数据放在URL也就是网址里)
==安全性低
==容量低
==用于获取数据(如：浏览帖子)
==get的好处：找到一个好的帖子什么的，你只要的到他的网址。就能在任何地方打开了 便于分享
(2)POST方法 (他不是把数据放在URL里，是放在http content里)
==安全性一般
==容量无限
==用于提交数据(如：提交表单)
#####Ajax编写
==先知道Ajax请求的步骤
==1、创建Ajax对象  2、链接服务器  3、发送请求  4、接收返回
(1)创建Ajax对象
var oAjax=new XMLhttpRequest();（不支持IE6）
var oAjax=new ActiveXObject("Microsoft.XMLHTTP");(在IE6中以插件的形式创建)
==兼容处理
```
         
``` var oAjax=null;
		 if(window.XMLHttpRequest){ //(因为XMLHttpRequest作为变量在IE6上是报错的 所以要把它变成属性)
			var oAjax=new XMLHttpRequest();（不支持IE6）
		 }else {
			var oAjax=new ActiveXObject("Microsoft.XMLHTTP");(在IE6中以插件的形式创建)
		 }
(2)链接服务器
==只需一个 open(方法,URL,是否异步);函数
```
oAjax.open("GET","调试可先使用wamp里www的文件路径代替"，ture)

同步：在js中同步是每件事不能一起做，要一件件来
异步：在js中异步是可以多件事可以一起做
```
(3)发送请求
```
oAjax.send();
```
(4)接收请求
```
oAjax.readyState属性有以下五个值 （请求状态）
    0：(为初始化)还没定义open()方法
    1：(载入)已调用send()方法，正在发送请求
    2：(载入完成)send()方法完成，已收到全部相应内容 
    3：(解析)正在解析响应内容
    4：(解析完成)响应内容解析完成，可以在客户端调用了(只能说是完成 不代表成功)
oAjax.status属性  (请求结果 通过它知道是否成功)
   200：成功
   ==其他的都是失败  有个常见的404 
oAjax.onreadystatechange=function()  (这个事件是：当这个Ajax于服务器那边有通信或有状态变化的时候发生)
{
	if(oAjax.readyState==4)
	{
	    if(oAjax.status==200)
	    {
            alert(oAjax.responseText);\\(接收到的内容)
     	}
     	else
     	{
            alert("失败");
     	}

     }
}
```
#####封装
```
function myoAjax(url,chengong,shibai)
{
	 var oAjax=null;
     if(window.XMLHttpRequest);
      { 
			oAjax=new XMLhttpRequest();
	  }
	  else 
	  {
			oAjax=new ActiveXObject("Microsoft.XMLHTTP");
	  }
	  oAjax.open("GET",url,ture);
      oAjax.send();
    oAjax.onreadystatechange=function()
    {
	if(oAjax.readyState==4)
	{
	    if(oAjax.status==200)
	    {
            chengong(oAjax.responseText);
     	}
     	else
     	{
     	    if(shibai)
     	    {
                 shibai();
             }
     	}

     }
     }
}

```
####二、WampServer
1、WampServer是什么
---Wamp就是Windows Apache Mysql PHP<font color="red"><b>集成安装环境</b></font>，即在window下的apache、php和mysql的服务器软件
--WampServer是一款由 <font color="red">法国人</font> 开发的Apache Web服务器、PHP解释器以及MySQL数据库的整合软件包
---语言：wampserver[2] 支持22种语言，其中有中文简体和中文繁体（安装并启动后右键托盘图标即可轻松更改）。
---特点：
(1)支持中文语言，一键安装，省时省力；任何人都可以轻松搭建；

(2)集成Apache/MySQL/PHP/PhpMyadmin；支持PHP扩展、Apache的mod_rewrit；

(3)一键启动、重启、停止所有服务，一键切换到离线状态等等。

---支持:wampserver还支持phpmyadmin,SQLiteManager。不用去输入复杂的SQL语句管理MYSQL数据库，直接从phpmyadmin管理即可。

####使用Ajax读取数据
1、缓存
--缓存就是浏览器浏览的网页只读取一次,然后就存在本的了，第二次第三次就是从本的读取了，所以第一次慢 后面快
直到重启浏览器 甚至
--弊端：服务器变化了有时客户端读取的还是旧的内容

###课程二(传智播客)
#####1、Ajax 是什么
==它是多种技术和思想的融合体
(1)使用XHTML和CSS的基于标准的表示技术
(2)使用DOM进行动态显示和交互(实现刷新页面一部分的功能)
(3)使用XML和LT进行数据的交互和处理(XML并不要一定要用到  XSLT是转化HTML文档的语言 jQuery就是用了它)
(4)使用XMLHttpRequest进行异步数据检索(异步交互才是Ajax最核心的功能)
(5)使用JavaScript将以上技术融合在一起
#####2、同步、异步
(1)同步：一个时间只能做一件事。发送出一个请求后就要等待服务器返回结果了 不能做其他事情
(2)异步：一个时间能做多个事情。发送出一个请求之后。可以看其他的东西。不用看着圈圈等待了(返回的页面先是XMLHttpRequest接收 在通过相应的程序呈现给用户)
#####传输模式
(1)传统传输模式：该模式http的请求，和服务器的回应是直接通过浏览器来完成的，同时传输的也是整个页面	
(2)基于Ajax的传输模式:该模式http(s)协议的传输是通过Ajax引擎完成的，服务器端的响应结果是一些数据(会经过Ajax引擎处理成一些XML等文本数据)，而不是整个页面
#####学前准备(重要到次要)
(1)XMLHttpRequest对象：解决了异步交互的问题
(2)javascript语言：Ajax技术的桥梁 json格式
(3)DOM:获取页面数据，解析服务器数据，无刷新页面更新
==不重要的
(4)XML技术：能够组织XML的数据就行
(5)HTML CSS等
(6)web标准和浏览器的差异
