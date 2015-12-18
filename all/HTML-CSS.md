title: "HTML+CSS"
date: 2015-04-13 15:18:36
tags: HTML+CSS
categories: 学习
---
###各种版本的doctype
```
html4.01：HTML 4.01 规定了三种文档类型：Strict、Transitional 以及 Frameset。

1、<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "
    http://www.w3.org/TR/html4/strict.dtd">

2、<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "
   http://www.w3.org/TR/html4/loose.dtd">

3、<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "
   http://www.w3.org/TR/html4/frameset.dtd">

xhtml1.0：XHTML 1.0 规定了三种 XML 文档类型：Strict、Transitional 以及 Frameset。

1、<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" 
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

2、<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

3、<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">

html 5：DOCYYPE声明：<!DOCTYPE html> 就行 不用以前那么多的声明了
```
HTML中插入字符：
      字符映射表  每个字符对应一个U+ 一个值的十六进制编号，可以用计算器转化为十进制，在HTML中输入&#加上这个数值 封号结束,有的有实体名称的可以直接输入&加他的名字 如&#+62实体编号（&lt实体名称） 显示的就是 >

8.5 Named character references — HTML5.htm
###HTML5
```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>

</body>
</html>
```
####一、新增元素
```
html5中的结构标签本质上是有意义的DIV标签
1、结构元素：

      header  元素表示页面中的一个内容区块或者整个页面的标题  ;<header></header>

      nav     元素表示页面中导航链接部分;                          <nav>...</vav>

      article 元素表示页面中的一块与上下文不相关的独立内容，比如一篇文章中的文章              
              <article></article>

      section 表示页面中的一块内容区域，比如章节的页眉，页脚等等。也可与h1~h6一起使用，标示出 
              文档的结构<section></section>(section嵌套一个就降一级)

      aside   元素表示article元素的内容相关的辅助信息<aside></aside>

      footer  表示页面或者页面中的一块的页脚，比如存放文件的创建时间、作者、联系方式等等。

              <footer></footer>

2、普通元素

      hgroup元素用于对整个页面或页面中一个内容区块的标题进行组合 ;<hgroup>...</hgroup>

      figure元素表示一段独立的流内容，一般表示文档主体流内容中的一个独立单元。

            使用 figcaption元素为figure元素组添加标题。

<figure>

<figcaption>PRC</figcaption>

<p>The People's Republic of China was born in 1949...</p>

</figure>

HTML 4中代码示例：

<dl>

<dt>PRC</dt>

<dd>The People's Republic of China was born in 1949...</dd>

</dl>

3、视频元素（好像不支持IE）

   <video src="movie.ogg" controls="controls">可写入不支持该标签的浏览器</video>

   支持 .ogg 、 .MPEG 4 格式     controls：属性供添加播放、暂停和音量控件。

   video 元素允许多个 source 元素。source 元素可以链接不同的视频文件。浏览器将使用第一个可识别
的格式 例如：

            <video width="320" height="240" controls="controls">
                 <source src="movie.ogg" type="video/ogg">
                 <source src="movie.mp4" type="video/mp4">
             Your browser does not support the video tag.
            </video>

   在html4中要用<object>标签

4、音频元素（好像不支持IE8之前）

    <audio src="song.ogg" controls="controls">可写入不支持该标签的浏览器</audio>

    支持Ogg Vorbos 、MP3 、Wav ; controls：属性供添加播放、暂停和音量控件。

                                       autoplay属性：音频就绪后马上播放

                                       proload属性：在页面音频加载时进行加载并预备播放

    audio 元素允许多个 source 元素。source 元素可以链接不同的音频文件。浏览器将使用第一个可识别的格式  例如：

            <audio controls="controls">
                <source src="song.ogg" type="audio/ogg">
                <source src="song.mp3" type="audio/mpeg">
             Your browser does not support the audio tag.
            </audio>

     在html4中要用<object>标签

5、embed：必须有src  没有结束标签   <embed src="horse.wav" />

   有四种属性：width、height、src、type

6、mark:<mark> 标签定义带有记号的文本。请在需要突出显示文本时使用 <mark> 标签。//相当于span

7、time：<time datetime="2008-02-14">情人节</time>或<time>9:00</time>

   datetime：定义元素的日期和时间。如果未定义该属性，则必须在元素的内容中规定日期或时间。
 
8、canvas 画布：<canvas> 标签定义图形，比如图表和其他图像。
```
<canvas id="myCanvas"></canvas>

<script type="text/javascript">

var canvas=document.getElementById('myCanvas');
var ctx=canvas.getContext('2d');
//先给笔设置颜色
ctx.fillStyle='#FF0000';
//画出一个矩形
ctx.fillRect(0,0,80,100);

</script>

argb(d d d 透明度)

cxt.font="字宽 size "字体1"，"字体2"，"字体3";


绘制文字 0,0 文字相对于画布顶部横线的位置(垂直对齐方式)
cxt.textBaseline="(top 下) (bottom 上) (Middle 中) (alphabetic 中上) (hanging 中下) ";

绘制文字 0,0 文字相对于画布左边横线的位置(水平对齐方式)
cxt.textAlign="(start left 右)(end right 左)(center 中)";

cxt.fillText=("文字",x,y,100(防止溢出 所有内容必须在100px内王成));

createjs库文件：createjs.com (EASELjs(canvas用的)，TWEENjs(调整动画和js属性)，SOUNDjs(处理音频))


```
9、<output> 标签定义不同类型的输出，比如脚本的输出。//也相当于span

10、<source> 标签为媒介元素（比如 <video> 和 <audio>）定义媒介资源。//相当于param  参数设置

    media ：media query   定义媒介资源的类型，供浏览器决定是否下载。 
   
    src：   url           媒介的 URL。 
   
    type：  numeric value 定义播放器在音频流中的什么位置开始播放。默认，音频从开头播放。 

11、menu：html4中不支持使用  html重新启用  

<menu>
<li><input type="checkbox" />Red</li>
<li><input type="checkbox" />blue</li>
</menu>

属性：
      属性         值
    autosubmit  true false          如果为 true，那么当表单控件改变时会自动提交。   5 
    compact     compact_rendering   不支持。请使用 CSS 代替。 4   
    label       menulabel           为菜单定义一个可见的标注。   5 
    type        context             定义显示那种类型的菜单。默认值是 "list"。   5 
                toolbar 
                list 
 

12、不建议使用框架 支持浮动框架iframe

13、SVG
```
==SVG指的是可伸缩矢量图形

==SVG用来定义用于网络的基于矢量图形

==SVG用XML格式定义图型

==SVG图像放大缩小是不会损伤图像质量

==SVG遵循万维网标准

优势：

==它是可以通过编辑器来编辑修改的

==可以被搜索、索引、脚本化或压缩

==是可伸缩的

==任何分辨率都能高质量的打印出来

==放大质量不会下降

使用SVG必须在头部引入XML 文档类型  引入外部SVG文件可通过 iframe src属性
```
14、HTML5中客户端储存数据的两种方式
```
1、localStorage：该方法储存的数据没有时间限制，不管多久以后数据依然可用
2、sessionStorage：针对session进行数据储存，当用户关闭浏览器是数据就会被删除
```
15、应用缓存
```
1、就是说 只要访问过的网页 就可以在没有因特网的情况下进行查看了
2、优势：
  (1)离线浏览         用户可以在离线的情况下使用它们
  (2)速度             已经缓存的资源加载数度更快
  (3)减少服务器负载   浏览器只从服务器下载更新过或加载过的资源
3、实现缓存
   如果要启用缓存，就要在<html>中包含manifest属性  建议使用的扩展名是  .appcache ;
   如：《html manifest="index.appcache"》 然后在 index.appcache 中写入代码
4、manifest文件
   CACHE MANIFEST  在此标题下的文件首次下载后能进行缓存
   如：
   CACHE MANIFEST

   CACHE:
   文件名1.后缀名
   文件名2.后缀名
   文件名3.后缀名

   NETWORK         在此标题下的文件需要与服务器连接 而且不会被缓存
   如：
   直接 NETWORK:
        文件名.后缀名
   
   FALLBACK        在此标题下的文件规定当页面无法访问时到的页面（比如404页面）
```
16、Web Worker
```
1、web worker是运行在后台的JavaScript脚本，独立于其他脚本 不会影响页面性能

2、方法：
postMessage() 它用于向页面回传一段消息
terminate() 终止 web worker 并释放浏览器/计算机资源

3、事件：onmessage
```
17、jQuery(jQuery.com)
```
1、通过script标签 引入jQuery

==可以直接引入网站上的jQuery地址 如谷歌的

==推荐自己下载下来直接引入 地址：jQuery.com

2、jQuery是js的函数库(他对js代码进行了封装  甚至封了对浏览器的兼容性问题)

3、jQuery函数库的功能
   
    (1)HTML元素选取
    (2)HTML元素操作
    (3)css操作
    (4)HTML事件函数
    (5)JavaScript特效和动画
    (6)HTML遍历和修改
    (7)Ajax
    (8)Utilities

4、基础语法
==基础语法格式：$(selector).action()
==$符号是定义jQuery
==(selector) 查询和找出html元素
==jQuery的action执行对元素的操作
例如：
$(this).hide();隐藏当前元素
$("p").hide()；元素隐藏当前段落
selector里放的是选择符
5、jQuery事件
==常用事件方法：
==绑定事件：
-$(selector).bind("事件"，方法);然后在rady外面定义这个方法与功能就行了
.unbind是解除绑定
1.7版本之后可用.on与.off代替它们

引入：

通过script标签引入jQuery
在引入自己的js文件(jQuery文件一定要在上面)

在自己的js文件里：
$(document).ready(function()  //确保文档是加载完全的 相当于 window.onload
{
  

});

```
####二、新增属性


###陌生属性或标签
1、透明度
对象.style.filter="alpha(opacity:"0~100")";
对象.style.opacity=0~1;
CSS中：
filter:alpha(opacity:0~100);
opacity:0~1;
-moz-opacity:0.5;（提供给火狐用的）

2、强制不换行:white-space:nowrap





