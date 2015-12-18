title: "JSON"
date: 2015-05-02 23:53:02
tags: JSON
---
####简介
==js在js中就是一个对象：格式：{"firstName":"zhi","Array":[.......],"Emali":"869664233@qq.com"}(是一个名称/值对集合)
==json是js的原生格式，所以在js中处理json不需要任何的API或或工具包

####JSON与XML
==一般来说json是轻量级的数据交换格式 ------>XML是标准或业界的数据交换格式
![区别](JSON/json.jpg)

####服务器端处理json响应
==如果服务器返回json：{"city":"Hefei","province":"Anhui"}
==客户端使用eval()将json文本转化为JavaScript对象：var response=eval("("+requesr.responseText+")");


