title: "cookie"
date: 2015-04-09 12:03:49
tags: cookie
categories: 学习
---
cookie 是存在客户端浏览器下的数据
cookie 是属于document下的。它是由一个个字符串构成
作用：用来在客户端上保存信息 如:自动登入 保存信息等
特性：同一个网站上所有的页面是共享一个cookie的
cookie的数量大小是有限的 不会很多 也不会很大
cookie有过期时间(由js控制)
cookie:只能在火狐或服务器端运行
cookie中等号代表添加不是复制 （就是 document.cookie="user=xingm" document.cookieh后面的等号）

格式：
var oDate=new Date();

oDate.setDate(oDate.setDate()+30);//设置的日期是当前日期+30

document.cookie="user=username;expires="+oDate;//代表30天后过期
```
封装：
function setCookie(name,value,day)
{
   	var oDate=new Date();
   	oDate.setDate(oDate.setDate()+day);
   	document.cookie=name+"="+value+";expires="+oDate;
}

获取：
function getcookie(name)
{
	var arr=document.cookie.split(";");
	for(var i=0;i<arr.length;i++)
	{
	   var arr2=arr[i].split("=");
	   if(arr2[0]==name)
	   {
	     return arr2[1];
	   }

	}
	return "";

}
删除：
function removecookie(name)
{
	setCookie(name,"hgdr",-1);
}
```