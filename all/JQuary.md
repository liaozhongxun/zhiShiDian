title: "JQuary"
date: 2015-05-02 09:28:04
tags: jQuery
---
相关网址：[jQuery笔记](http://www.360doc.com/content/11/0825/17/4553438_143237155.shtml)
----
####jQuery与js
#####对应关系
===window.onload==$();
===window.onload=function(){};==$(function(){});
===this==$(this);
===innerHTML==html();
#####原生js于jQuery可以共存当不能混用
===共存
$("#div").html();
oDiv.innerHTML;
===混用
$("#div").innerHTML;
oDiv.html();
####常用的功能
==强大的过滤器
$("div").has("p");//选择包含p元素的div元素
$("div").not(".myClass");//选择没有.myclass类的div元素
$("div").filter(".myClass");//选择class等于.myClass的div元素
==相邻元素查找
$("div").next("p");//选择div元素后面的第一个p元素
$("div+")//div元素的下一个元素(两个+就下两个 +后面也跟选定的标签)
$("div").parent();//选择div元素的父元素
$("div").children();//选择div元素多有子元素
==链式操作
=$("div").find("h3").ep("2").html("Hello");
$("div")//找到div
.find("h3")//选择其中的 h3 元素
.ep("2")//选择第三个 h3 元素（从0开始）
.html("Hello");//将内容改为 Hello
.end//是"结果集"后退一步（子在设置其他属性）
==取值与复制合体
$("h1").html();//html()没有参数表示取出h1的值
$("h1").html("hello");//表示复制
=扩展
.val()//获取value值  --设置value值
.attr()//获取属性    --一个参数就是获取 两个参数就是设置
.prop()//.attr获取的是标签对里的value  .prop获取的可以是在页面上改动的value
.width()//获取宽和设置宽
获取宽度
.innerWidth() //获取中间宽度+margin的宽度
.outerWidth()//获取中间宽度+padding的宽度+border宽度
.outerWidth(true)//获取中间宽度+padding的宽度+border宽度+marhin的宽度

=取值是去第一个的值，复制是给所有获取到的赋值
==元素移动
$("div").insertAfter($("p"));//把div元素移动到p元素后面
$("div").appendTo($("p"));
$("p").after($("div"));//把p放到div前面
$("div").append($("p"));
区别是操作元素的不同
.前面加.clone()就可看做复制了
==jQuery的创建
$("#ul").append("<li>aaaa</li>");
相当于
var oLi=$("<li>")
oLi.html("aaaa");
$("div").append(oLi); 
==工具方法(原生js也能用)
$.trim() 去除字符串两端的空格。  
    
$.each() 遍历一个数组或对象。  
    
$.inArray() 返回一个值在数组中的索引位置。如果该值不在数组中，则返回-1。  
    
$.grep() 返回数组中符合某种标准的元素。   
    
$.extend() 将多个对象，合并到第一个对象。   
    
$.makeArray() 将对象转化为数组。  
    
$.type() 判断对象的类别（函数对象、日期对象、数组对象、正则对象等等）。  
    
$.isArray() 判断某个参数是否为数组。  
    
$.isEmptyObject() 判断某个对象是否为空（不含有任何属性）。  
    
$.isFunction() 判断某个参数是否为函数。  
    
$.isPlainObject() 判断某个参数是否为用"{}"或"new Object"建立的对象。  
    
$.support() 判断浏览器是否支持某个特性。
==时间
=独立事件：$("div").click(function(){语句}); （不要on）
.blur() 表单元素失去焦点。  
    
.change() 表单元素的值发生变化  
    
.click() 鼠标单击  
    
.dblclick() 鼠标双击  
    
.focus() 表单元素获得焦点  
    
.focusin() 子元素获得焦点  
    
.focusout() 子元素失去焦点  
    
.hover() 同时为mouseenter和mouseleave事件指定处理函数  
    
.keydown() 按下键盘（长时间按键，只返回一个事件）  
    
.keypress() 按下键盘（长时间按键，将返回多个事件）  
    
.keyup() 松开键盘  
    
.load(url,) 元素加载完毕  
    
.mousedown() 按下鼠标  
    
.mouseenter() 鼠标进入（进入子元素不触发）  
    
.mouseleave() 鼠标离开（离开子元素不触发）  
    
.mousemove() 鼠标在元素内部移动  
    
.mouseout() 鼠标离开（离开子元素也触发）  
    
.mouseover() 鼠标进入（进入子元素也触发）  
    
.mouseup() 松开鼠标  
    
.ready() DOM加载完成  
    
.resize() 浏览器窗口的大小发生改变  
    
.scroll() 滚动条的位置发生变化  
    
.select() 用户选中文本框中的内容  
    
.submit() 用户递交表单  
    
.toggle() 根据鼠标点击的次数，依次运行多个函数  （括号里可以放多个函数）
    
.unload()  
    
=通用事件：(所有事件都具备的方法)
```
使用.bind()可以更灵活地控制事件，比如为多个事件绑定同一个函数：
 
$('input').bind('click change',<!--同时绑定click和change事件 --> function(){ alert('Hello');} );  

有时，你只想让事件运行一次，这时可以使用.one()方法。
   
$("p").one("click",function(){ alert("Hello"); });<!-- 只运行一次，以后的点击不会运行 --> 

.unbind()用来解除事件绑定。
    
$('p').unbind('click'); 

所有的事件处理函数，都可以接受一个事件对象(event object)作为参数，比如下面例子中的e：

$("p").click(function(e){ alert(e.type); //"click"}); 


这个事件对象有一些很有用的属性和方法：

event.pageX 事件发生时，鼠标距离网页左上角的水平距离

event.pageY 事件发生时，鼠标距离网页左上角的垂直距离

event.type 事件的类型(比如click)

event.which 按下了哪一个键

event.data 在事件对象上绑定数据，然后传入事件处理函数

event.target 事件针对的网页元素

event.preventDefault() 阻止事件的默认行为(比如点击链接，会自动打开新页面)

event.stopPropagation() 停止事件向上层元素冒泡

return false;既组织默认事件 有组织冒泡

在事件处理函数中，可以用this关键字，返回事件针对的DOM元素：

$('a').click(function(){  
    
                 if ($(this).attr('href').match('evil')){//如果确认为有害链接  
    
                 e.preventDefault(); //阻止打开  
    
                 $(this).addClass('evil'); //加上表示有害的class  
    
                     }  
});  

有两种方法，可以自动触发一个事件。一种是直接使用事件函数，另一种是使用.trigger()或.triggerHandler()。

$('a').click();

$('a').trigger('click');
```
==特殊效果

jQuery允许对象呈现某些特殊效果。
  
1、$('h1').show(); //展现一个h1标题 

常用的特殊效果如下：

.fadeIn() 淡入

.fadeOut() 淡出

.fadeTo() 调整透明度

.hide() 隐藏元素

.show() 显示元素

.slideDown() 向下展开 (括号里能放时间 指定多久王成)

.slideUp() 向上卷起

.slideToggle() 依次展开或卷起某个元素

.toggle() 依次展示或隐藏某个元素

除了.show()和.hide()，所有其他特效的默认执行时间都是400ms(毫秒)，但是你可以改变这个设置。


    
1、$('h1').fadeIn(300); // 300毫秒内淡入  
    
2、$('h1').fadeOut('slow'); //缓慢地淡出 


在特效结束后，可以指定执行某个函数。
   
1、$('p').fadeOut(300, function(){$(this).remove(); }); 

更复杂的特效，可以用.animate()自定义。

$('div').hover(function(){

       	 $(this).stop().animate({  //stop()作用是清楚之前的运动效果

       	    width:300,

       	    height:500});

       	},function(){

       	$(this).stop().animate({

       	 width:200,

       	 height:200});

       });

.animate({ 语句  })
.stop()和.delay()用来停止或延缓特效的执行。

$.fx.off如果设置为true，则关闭所有网页特效。

==UI组件
进入官网 ui项下载UI或复制网址
引入jQuery文件 
在通过script引入相应的组件(你需要的功能)
按照他下面提供的方法执行就行了
==选择器：
```
1、基本选择器
*  id  class  元素  多选(跟CSS中写法一样)

2、层级选择器
后代(ul li)(ul下的所有 不管多少层)
子(ul > li)(ul下的第一代li)
相邻(ul+p)(选的是ul同级的下一个p标签)
兄弟(ul~p)(ul同级的下面所有的p标签)

3、筛选选择器(以冒号开头 基于前面的选择器选到的标签)

(1):first             (选择第一个（只能选一个父元素下的一个）)
===:first-child       (选择第一个（能选多个父元素下的子元素）)
(2):last              (选择最后一个 只能选一个父元素下的一个)
===:last-child        (选择最后一个 能选多个父元素下的一个)
(3):not(选择符)       (不要选选择符)
(4):even              (把选中的从零开始排 只要偶数的)
(5):odd               (把选中的从零开始排 只要奇数的)
(6):eq(index)         (把选中的从零开始排 选择索引指定的)
(7):gt(index)         (把选中的从零开始排 选择大于索引指定的)
(8):lt(index)         (把选中的从零开始排 选择小于索引指定的)
(9):header            (选择标题 h1 标签)
(10):animated         (选择正在运动的标签)
(11):focus            (选中有焦点的标签)
(12):root             (html标签)
(13):contains(text)   (选择包含括号里面内容的标签)
(14):empty            (选中空标签)
(15):has(选择符)      (选择包含这个 选择符 的父元素)
(16):parent           (选择有父节点的子节点)
(17):hidden           (选择jQuery认为不可见的标签)
4种：1、display:none  2、表单元素type为hidden 3、宽高为零  4、父元素是前面三种之一
不算的
像透明度为零
visibility：hidden
(18):visible          (和17相反 选的是可见的元素)
 不包括 option

 4、属性选择器
 (1)[attribute]        (直接写一个属性 有这个属性的元素 都会被选中)
 (2)[attribute=value]  (页面上所有 这个属性等于这个值得元素)
 (3)[attribute!=value] (页面上所有 这个属性不等于这个值得元素)
 (4)[attribute*=value] (获取指定属性值中包含指定内容的元素 value的值就是指定的值)
 (5)[attribute^=value] (获取页面上这个属性的值 是以指定的value开头的元素)
 (6)[attribute$=value] (获取页面上这个属性的值 是以指定的value结尾的元素)
 (7)[attribute*=value] (获取指定属性值中包含指定内容的元素 value的值就是指定的值)
 (8)[attribute*=value] (获取指定属性值中包含指定内容的元素 value的值就是指定的值)
 (9)[attrSel1][arrtSel2] (可以有多个是与的关系 会选中同时拥有这些属性的元素)

 5、子筛选选中器
 (1):first-child              (选择第一个（能选多个父元素下的子元素）)
 (2):last-child               (选择最后一个 能选多个父元素下的一个)
 (3):nth-child(从一开始的数)  (父节点下选中指定的的几个元素)
 (4):only-child

 6、表单选中器
 (1):input(选中所有的表单元素)
 (2):text(只选中type= text 的input)
 (3)()
 (4)()
 (5)()
 (6)()
 (7)()
 (8)()
 (9)()
 (10)()
 (11)()
```
==其他功能
$("div").css("属性","改成怎样");//一个参数就是获取 两个参数就是设置(相应操作与样式有关)
$("div").hide();隐藏
$("div").show();显示



####jQuery选择符
#####CSS选择符方式
-------------------------
关于鼠标
1、禁用右键菜单
document.oncontextmenu=function(){retutn false;}
2、e.which=1、2、3分别是鼠标的左中右三个键
3、e.clientX \ Y;获取鼠标的坐标

关于背景
1、获得图片或图片背景路径
在要操作的对象上加上一个自定义属性值为 要获取的图片的路径
find("该对象").attr("该自定义属性") (具体怎样看具体布局)
--------------------------
1、放大镜效果
