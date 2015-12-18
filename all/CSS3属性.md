title: "CSS3属性"
date: 2015-05-04 21:32:52
tags:
---
##分类
###CSS3属性选择器
###CSS3构造伪类选择器
###CSS3UI元素状态伪类选择器
###CSS3其他选择器

##新增属性(杂)

==浏览器内核前缀:IE9(ms)、Firefox(moz)、Safari and Chrome(webkit)、Opera(o);

1、(1) 阴影:box-shadow:水平方向 垂直方向 模糊程度px表示 扩展值 颜色 inset(设置阴影为内阴影)
       不兼容的浏览器用法:-webkit（各浏览器内核前缀）-box-shadow: ;放在标准的上面(如果在js中设置 用boxShadow表示)
       设置多种颜色:设置多次，每次用逗号隔开，通过扩展值得不同来显示多种颜色。
   
   (2) 倒影:box-reflect:none 或 位置 偏移(本身与倒影的距离) 水印图片或渐变;(偏移和水印图片可有可无)
       不兼容的浏览器用法:-webkit（各浏览器前缀）-box-reflect: ;放在标准的上面
       位置的属性:above(上) below(下) left(左) right(右)
       偏移： 用长度值来定义倒影与对象之间的间隔。可以为负值
       水印图片: 设置倒影使用的图片或者渐变，默认为原内容
       注意:该属性目前仅webkit内核浏览器(chrome/safari/猎豹等)支持

   (3) 渐变:linear-gradient



2、边框
(1)边框图片：有五种属性设置边框图片不会影响div的宽高（在谷歌上会固定增加三像素）
例子：
border-image：
border-image-source:默认none、URL;(图片路径)
border-image-width:1px;(设置边框宽度)
border-image-slice:1px fill;(切割方式)(加上fill就能显示中间内容不分了)
border-image-outset:1px ;(扩展)
border-image-repeat:stretch(默认)、repeat(不自动取整的平铺)、round(自动取整的平铺)、space;

(2)圆角
==javasctipt语法:object.style.borderRadius="5px"

border-radius:10px/10px==10px;(横向和纵向都离边10px开始画圆角)(因为只设定一个参数所有同事设定四个角)
border-radius:四个角的水平半径/四个角的垂直半径; (从左上开始)
border-top-left-radius:水平方向半径 垂直方向半径：下同
border-top-right-radius
border-bottom-right-radius
border-bottom-left-radius

3、背景

(1)背景大小
background-size:宽 高;

(2)背景位置
==javascriot语法:object.style.backgroundOrigin="content-box"

background-origin 属性规定 background-position 属性相对于什么位置来定位。
background-origin:
值: padding-box 背景图像相对于内边距框来定位。 
    border-box 背景图像相对于边框盒来定位。  
    content-box 背景图像相对于内容框来定位。 

background-clip 属性规定背景的绘制区域。
background-clip: border-box|padding-box|content-box;(超出相对范围就会被裁减)

4、文本效果

(1)文本阴影

text-shadow:水平位置 垂直位置 模糊程度 颜色;(值以逗号的形式创建多个阴影)
css3新增颜色方法:rgba(红,绿,蓝,透明度);

=text-overflow使用前提是 overflow:hidden; 和white-space:nowarp;
text-overflow:ellipsis;(溢出的部分用省略号代替 clip属性是默认属性 )

text-align:left ：默认值 内容左对齐。
           center：内容居中对齐。
           right： 内容右对齐。
           justify： 内容两端对齐。写本文档时仅Firefox能看到正确效果
           start： 内容对齐开始边界。（CSS3） 左对齐
           end： 内容对齐结束边界。（CSS3） 右对齐 （有 direction:rtl;unicode-bidi:bidi-override; 就相反）

text-fill-color:颜色;(特殊值绝对透明的transparent属性)
text-storke:描边大小 描边颜色;(这两个需要加浏览器私有前缀)

tab-size:一个整数 不需要px;设置改容器内的tab长度（火狐和欧朋用的是长度值 需要些px）



允许长单词换行到下一行：
word-wrap: normal|break-word;
normal 只在允许的断字点换行（浏览器保持默认处理）。 
break-word 在长单词或 URL 地址内部进行换行。

5、css3新增颜色属性
rgba(r,g,b,a) a的取值是0~1;
hsl(色调,饱和度,亮度);(色调是0~360的字体 参照色轮位置)
hsla(色调,饱和度,亮度,透明度);

6、利用伪类变大小(需要加浏览器私有前缀)
transform:scale(1.1); 变大1.1倍
          rotate(0deg);2d旋转 参数设置角度

transition:all 时间 linear; 和上面的一起用是对象自然的变大

<!-- 动画设置 -->
animation: name duration timing-function delay iteration-count direction;
<!-- 各属性的值 -->
animation-name 规定需要绑定到选择器的 keyframe 名称。。 
<!-- 值:和定义好的动画相同 -->
animation-duration 规定完成动画所花费的时间，以秒或毫秒计。
<!-- 值:一个时间 -->
animation-timing-function 规定动画的速度曲线。 
<!-- 值:linear 动画从头到尾的速度是相同的。 测
        ease 默认。动画以低速开始，然后加快，在结束前变慢。
        ease-in 动画以低速开始。 
        ease-out 动画以低速结束。 
        ease-in-out 动画以低速开始和结束。 
        cubic-bezier(n,n,n,n) 在 cubic-bezier 函数中自己的值。可能的值是从 0 到 1 的数值。  -->

animation-delay 规定在动画开始之前的延迟。 
<!-- 值:时间 -->
animation-iteration-count 规定动画应该播放的次数。
<!-- 值:n 定义动画播放次数的数值。 
        infinite 规定动画应该无限次播放。  -->

animation-direction 规定是否应该轮流反向播放动画。 
<!-- 值:normal 默认值。动画应该正常播放。 
        alternate 动画应该轮流反向播放。 
 -->

<!-- 动画定义 -->
格式:@-webkit-keyframes 动画名{}
旋转动画：
@-webkit-keyframes rotae{
  from{-webkit-transform:rotate(0deg)}
  to{-webkit-transform:rotare(360deg)}
}













##js中使用
1、中设置CSS样式：
对象.style.cssText=""；(就能在字符串设置该对象的样式了 用字符串连接的方式使用变量)
2、Math.min.apply(null,arr);(Math.min()括号里是不能放数组的加了apply属性就能算数组里的最小值了)

