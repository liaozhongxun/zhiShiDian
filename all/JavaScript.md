layout: js
title: "JavaSctopt"
date: 2015-04-07 13:38:55
tags: JS
categories: 学习

---

###基础关键字
Object.valueOf();取出对象的值

Object.toString();将对象转化为字符串

str.chatAt(i) ：选取这个字符串的第i位数

setInterval（函数，毫秒数）   ：定时器 （每隔多少时间后执行一次）

setTimeout（函数,毫秒数）    ：（隔多少时间后执行一次 然后就不会执行了）

eval(str);:把字符串里的内容转化成JS代码

clearInterval（） ：关闭定时器

clearTimeout（）：关闭定时器
######offset

offsetLeft:改变定位的div的左边位置

offsetTop：               上边

offsetWidth：        div的宽度（包括本身的宽 padding 和边框）

offsetHeight：            高度    

parseInt：字符串转数字    

parseFloat 

Math.ceil(数值)：向上取整

Math.floor(数值):向下取整

Math.abs():绝对值

currentStyle:获取非行间样式（适合IE）

getComputedStyle（对象，false）；适合火狐 设置就直接Style就行了
```
兼容封装：

function getStyle(obj,attr)//表示获哪个对象的什么属性
{
    if（obj.currentStyle）
    {
        return obj.currentStyle[attr];
    }
    else
    {
         return getComoputedStyle(obj,false)[attr];
    }

}
var setShuXing=parseInt(getStyle(哪个对象，什么属性););
```
arr.puth(1);从尾部添加东西

arr.pop();  从尾部删除一个元素

arr.unshift(1);从头部添加东西
arr.shift();从头部删除东西

arr.sort();给数组排序（只认识字符串）

            排正确的数字

            arr.sort(  function(num1,num2){ 

                            return num1-num2;

                                           }
               
                      );

arr1.concat（arr2）;数组的链接（数字本身不变）
 
arr.join("连接数组的符号"); 数组连接符的设置（数组变成字符串）

str.split("决定从哪断的符号");把字符串变成数组

arr.splice();
 
             1、删  arr.splice(开始位置，删除的个数 )

             2、插  arr.splice(开始位置，删除 0 个，插入的元素1，插入的元素n)

             3、换  arr.splice(开始位置, 删除 n 个，插入n个)

####字符串应用

######获取

1、在js里汉字和字母和数字一样 一个只占一个字符 (其他语言不是)

2、str.charAt(数值)==str[数值](不兼容IE6) 输出这个位置所在的字符

3、str.charCodeAt(数值)   跟charAt一样 但它返回的是这个字符的ASCLL编码

4、String.fromCharCode   编码转化为字符  必须在String这个实例对象下使用

######查找

1、str.indexOf("一个字符")  返回这个字符串中第一个这个字符所在位置（可以是单个也能是多个 没有的话返回-1）

2、str.lastIndexOf("一个字符")  返回这个字符串中最后一个这个字符所在位置（可以是单个也能是多个 没有的话返回-1） 

3、str.search("一个字符")  也是返回这个字符的位置（但是他可以兼容正则 如果使用在字符串上，这个字符串出现一些正则的特殊符号他会报错 他是按照正则的方式解释的）

4、str.match (正则)  匹配和替换基于正则使用

5、src.replace("a","A"); 把a替换成A

######字符串比较 

--直接用str1< str2 这样是按照utf-8编码比较的

1、str1.localeCompare(str2) 按照当地人习惯比 （就是说如果内容是汉字就按拼音比，字母的话就按他的顺序比）

######截取

1、str.slice(开始位置，结束位置)  截取开始结束只见到的字符 包括开始 不包括结束

2、str.slice(只给他开始位置)   会取这个字符串的该位置到结束的所有字符

3、str.substring(开始位置，结束位置)  截取开始结束之间的字符 包括开始 不包括结束

4、str.substring(只给他开始位置)   会取这个字符串的该位置到结束的所有字符

--这两个函数参数是正的情况下是一样的，第一个如果是负的会从后面数，第二个会转化为0

5、str.substr(开始位置，结束位置) 跟substring 一样 但是他<font color="red">包括结束位置</font>

6、str.split("符号")  根据分隔符，拆分成数组

######大小写转化

1、str.toLowerCase(); 把字符串全部转化为小写

2、str.toUpperCase();把字符串全部转化为大写

###ＤＯＭ

####节点

document：document相当于在文档类型以上最外围的一个虚拟的节点

子节点：分为<font color=“0xff0000” >文本节点</font>和元素节点
  
childNodes：获取子节点（他是一个数组 一个节点的子节点只算他里面的一层 有的浏览器上包括文本节点）

nodeType:文本类型 

 nodeType==1 属于元素节点
 
 nodeType==3 属于文本节点

children：也是获取子节点 childNodes在有的浏览器下会取文本节点 children不会

######获取的一个子节点：

 firstChild：获取的一个子节点 （只能在IE上使用）

 firstElementChild：在火狐上获取第一个子节点

######获取最后一个子节点：

 lastChild：在IE上获取最后一个子节点

 lastElementChild：在火狐上获取最后一个子节点

######获取同级的节（兄弟节点）

 nextSibling、previousSibling：在IE上获取上一个 和 下一个兄弟节点

 nextElementSibling、previousElementSibling：在火狐上获取上一个 和 下一个兄弟节点

parendNode：获取父节点

offsetParent：获取有定位的父节点    还可获取无人在页面上的实际坐标

######元素方式操作元素
 1、oTxt.value="123"   用点操作属性

 2、oTxt["value"]="123"  用方括号操作属性  (可完全取代点的方式)

######DOM方式操作元素属性 
1、DOM方式：

 （1）oTxt.setAttribute("value","123")  把对象的 value属性值设置成 123

 （2）oTxt.getAttribute("属性")    获取的是这个属性的值

 （3）oTxt.removeAttribute("属性")  删除这个属性
 ######通过className选元素（在改变他的样式）

<b>封装</b>
       function getByClass(oParent,sClass)（从哪选，选哪个类）
         {
            var aEle=oParent.getElementsByTagName（"*"）;（*代表所有元素）
            var aResult=[]; 
            var i=0;

            for(i=0;i<aElem.length.i++)
            {
               if（aEle[i].className==sClass）
               {
                  aResult.push(aEle[i]);
               }
            }
            return aResult;
         }
使用： 

        变量=getByClass（oUl，"类名"）
          for（var i=0;i<变量.length;i++）
          {
            改变量[i]的样式；
          }

this：当前发生事件的对象
####创建元素并赋到也面上：
 
                 oLi=document.creareElement("li");(创建一个li作为子节点)

                 父节点.appendChild(子节点);

                 oUl.appendChild(oLi);将创建好的li赋到Ul中 (只能加在父节点的最后)

                 父节点.insertBefore(子节点，谁之前插入);(如果ali.lenght==0就出问题了 用if)
                      
                 oUl.insertBefore(oLi，ali[i]);将创建好的li赋到Ul中 (只能加在父节点的最后)

                 父节点.removeChild(删的是什么节点); this.parentNode;表示当前这个东西的父节点


####文档碎片：

      frag=document.createDocumentFragment() 理论上会提高dom性能

      用法：把前面的oUl改成frag 再把frag当做子节点赋到 oUl上

###BOM(操作浏览器 也就是Windows)
[window是document的上级 平常是可以省略的 表示在这个窗口显示]
==所有的全局变量 全局函数都可当做window下的属性 只是省略了window

==有无window的差别：用一个不存在的变量会出错。用一个不存在的属性出现undefined

(可用于Ajax的兼容处理)

#####一、一些常用方法
1、打开关闭窗口：Window.open("打开的地址（如一个网址）","打开方式")

2、清空当前页面并输出内容到页面上：document.write(""); 可以放代码

（变量=Window.open ("#"); 变量.document.write("s");就是让新打开的窗口显示 s）

3、关闭打开的当前的窗口：Window.close();

4、当前使用浏览器版本：Window.navigator.userAgent

5、(1)当前页面的网址：Window.location 
 
  （2）转到一个网页：Window.location="http://liaozhongxun.github.io"

6、可视区距离：document.documentEliment.clientWidth (可视区的宽度)

document.documentEliment.clientHeoght(可视区的高度)

7、滚动距离：(scrollTop是可视区到页面顶部的距离 scrollLeft可视区到左边顶部的距离)

document.body.scrollTop（Chrome下）

document.documentEliment.scrollTop（非Chrome下）

document.body.scrollLeft（Chrome下）

document.documentEliment.scrollLeft（非Chrome下）

8、系统对话框：

    alert（“值”）;弹出这个值只能确定

    confirm（“一个问题”） 可选是或否 给他一个返回值 a=confirm（“一个问题”）;a就是用户选的

    prompt("参数一是提示语"，"一开始的默认值")  a=prompt ... 返回的 也就是a的值是输入的内容

二、Window常用事件：

1、Window.onscroll=function(){} 当页面滚动的时候

2、Window.onresize  单页面重定大小的时候执行（拉动窗口的大小）

3、Window.onload    读取完整个页面的时候执行

###事件
######一、事件对象
事件对象：就是event对象 用event表示

--事件是作用于对象的，执行一个事件有什么样的功能取决于后面执行的函数
如：document.onclick=function(){“内容”} 
IE上事件对象是用event  火狐上是用后面函数传进去的参数（好像没有限制）

--兼容处理
1、document.onclick=function(ev){
	
	if（ev）{
		alert(ev.clientX+ ',' +ev.clientY);
	}else{
		alert(ev.clientX+ ',' +ev.clientY);
		}\\(因为传进去的参数在火狐上是true 在IE上是falsh)
}
2、document.onclick=function(ev){
	var oEvent=ev||evevt;\\(oEvent取真的值)
}

######EVEVT||传进去的参数：
oEvent.cancelBubble=ture;(阻止事件冒泡)
oEvent.clientX (鼠标可视区 X轴坐标)
oEvent.clientY (鼠标可视区 Y轴坐标)
oEvent.keyCode (按下哪个键就是那个键的键码)（用于键盘按下事件）
oEvent.ctrlKey  (然Ctrl键加另外一个键一起完成一个操作)
oEvent.shiftKey (然shift键加另外一个键一起完成一个操作)
oEvent.altKey   (然alt键加另外一个键一起完成一个操作)
#####DOM两种标准事件流
######事件冒泡（冒泡事件流）
--当事件在某有个DOM元素被触发时 事件将跟随该节点继续向其父节点传递穿过整个DOM节点层次 。直到最顶级
－－默认情况下使用冒泡事件流
1、阻止事件冒泡（通过事件对象的cancelBubble属性）
在事件函数里:
var oEvent=ev||evevt;(内容应该不用一定在中间)
oEvent.cancelBubble=true;
######鼠标事件
onClick  ：当单击时
onmousemove：当移动时
onmousedown：当鼠标按下时
onmouseup：当鼠标抬起时
######键盘事件
onkeydown：当键盘键按下的时候
onkeyup：当键盘按键抬起的时候
onpress：相当于onclick  是键盘按下并抬起的时候

######事件捕获（捕获事件流）
--从ＤＯＭ层次开始　而不是从事件目标元素，事件是从被触元素的祖先元素开始一次往下传递
######默认行为
--浏览器自身具备的
\\事件
==document.oncontextmenu=function(){}(右键菜单或环境菜单)
==阻止默认行为:在大括号里 return false；
阻止了默认事件可以让他按你的想法执行
######拖拽
涉及到三个事件
      onmousedown：存储距离
      按下时：
      得到鼠标到左边界的距离: Dx=oEvent.clientX-oDiv.offsetLeft
      得到鼠标到上边界的距离: Dy=oEvent.clientY-oDiv.offsetTop
     
      onmousemove：根据距离，计算div的最新位置(他在onmousedown里 最好给document加就不会甩掉了)
      让oDiv.style.left=oEvent.clientX-Dx+"px";
      让oDiv.style.top=oEvent.clientY-DY+"px";
      可以用if(oEvent.clientX-Dx<0){oEvent.clientX-Dx=0}的方法让他无法出页面 其他四边以此类推
      需要用到可视区的宽度：document.documentElement.clientWidth
      高度：document.documentElement.clientHeight 
      
      onmouseup: 这时候放开 (他在onmousedown里 最好给document加)
      直接让oDiv.onmousemove="null"; 

      如果div是空的在火狐低版本有一不支持。给onmousedown加个阻止默认事件就行了
####表单
==from的ID.onsubmit(当表单提交时执行)
####运动
1、普通运动
框架：
```
function YDFrame(MuBiao)
{
	var oDIV=document.getElementById("div");
	var times=null;
    
    clearInterval(times);
    times=serInterval(function(){
           var speed=0;
           if(oDIV.offserLeft>=MuBiao)
           {
				speed=-10;
           }
           else
           {
           		speed=10; 
           }
           
           if(Math.abs(oDIV.offserLeft-MuBiao<10))
           {
				clearInterval(times);
				oDIV.style.left=MuBiao+"px";
           }
           else
           {
           		oDIV.style.left=oDIV.offetLeft+speed+"px";
           }
    	},30) ;

}
```
2、缓冲运动
框架：
```
function YDFrame(MuBiao)
{
	var oDIV=document.getElementById("div");
	var times=null;
    
    clearInterval(times);
    times=serInterval(function(){
           var speed=(MuBiao-oDIV.offsetLeft)/10;(10这个书的大小要看具体情况)
           if(speed>0)
           {
           		speed=Math.ceil(speed);
           	} 
           	else
           	{
				speed=Math.floot(speed);
           	}
           
           if(oDIV.offserLeft==MuBiao)
           {
				clearInterval(times);
           }
           else
           {
           		oDIV.style.left=oDIV.offetLeft+speed+"px";
           }
    	},30) ;

}
```
3、多物体运动框架
###对象
#####1、工厂模式
==定义一个构造函数 1 原料(new 出一个对象)  2 加工(给对象加方法)   3 出厂(return返回)
function gouZhao(name,sex)
{
   1、new一个新对象
   2、赋值加工
      obg.name=name;
      obg.hans=function(){};
   3、return

};
==var ren=gouZhao("liao","nan");
给一个对象家方法(如数组)
==var arr1=new Array(1,2,3);
==var arr2=new Array(1,2,3,3);
==arr1.sun=funcuion(){};
==这样值给arr1加了sun方法
==Array.prototype(原型).sun=function(){};
==这样就是给数组加(arr1 arr2都能用了)
在js里面可以把类看出构造函数
==delete arr.a(删除给arr数组添加的a属性)

==instanceof  用来判断一个对象是不是这个类型的实例（如创建一个数组 arr，alert(arr instanceof Arrey),弹出的就是true)。
--------------
#JavaScript快速开发
##js的全局方法
ecodeURIComponent  把字符串编码为 URI 组件。
ncodeURI
ncodeURIComponent
val
sFinite
sNaN
arseFloat
arseInt
neval
nfinity
ntl


