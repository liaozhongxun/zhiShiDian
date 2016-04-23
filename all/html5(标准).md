title: "html5-CSS3"
date: 2015-05-04 21:32:52
tags:
---
【使用h5就要考虑到不兼容IE678】
升级的功能
1、html方面
(1)新增的HTML5标签
  ->结构标签(他带来的是网页布局的改变及提升对搜索引擎的友好)
  ->多媒体交互标签(有些以前就有的是浏览器厂商弄的不能通过w3c验证
                  是非标准的标签,html5中不需要验证了)
      <video> 标记定义一个视频
      <audio> 标记定义音频内容
      <source> 标记定义媒体资源

      <canvas> 标记定义图片

      <embed> 标记定义外部的可交互的内容或插件 比如flash
      HTML5的多媒体标签的出现意味着富媒体的发展以及支持不使用插件的情况下即可操作媒体文件，极大地提升了用户体验
  ->web应用标签
      [<menu>命令列表
      <menuitem>menu命令列表标签 FF（嵌入系统）
      <command> menu标记定义一个命令按钮

      <datalist> 为input标记定义一个下拉列表,配合option F、O
      <details> 标记定义一个元素的详细内容 ，配合dt、dd   C]--所有浏览器暂时不支持

      <meter>状态标签(实时状态显示:气压、气温)C、O
      <progress>状态标签 (任务过程:安装、加载) C、F、O

     
(2)删除的HTML标签(从html5的标准里删除的,但是还能用)

      纯表现的元素：
      basefont，big，center，font, s，strike，tt，u；

      对可用性产生负面影响的元素：
      frame，frameset，noframes；

(3)重新定义的HTML标签(标签还是以前的标签 只是意义改变了)
      <hr> 表示主题结束，而不是水平线，虽然显示相同


-----------------------------------------
1、结构标签
(新的结构标签跟div功能是一模一样的,但是他有意义搜索引擎能知道他)
2、媒体标签
   好处:1、不需要Flash等插件就能播放
        2、不需要传到优酷等网站
   坏处:1、要用自己的空间流量
   video:

       写法一:<video src="文件地址" controls="controls"></video>
             (controls是默认样式控件 没有的话就不能控制视频了)

       写法二:<video src="文件地址" controls="controls">
                您的浏览器暂不支持video标签。播放视频
              </video >
              (给IE678看的)

       写法三:<video  controls="controls"  width="300">
                  <source src="move.ogg" type="video/ogg" >
                  <source src="move.mp4" type="video/mp4" >
                  您的浏览器暂不支持video标签。播放视频
              </video >
              (兼容所有浏览器)
      支持 ogg MEPG4 WebM 

    audio:

      <audio src="文件地址" controls="controls"></audio>
      支持 ogg mp3 wav


       API自定义控件 (当怎样的时候执行什么方法 用js)
canvas:(画布)   

     <canvas id="huabu" width="" height=""></canvas>
     (该标签的宽高必须写在行间 在css中定义的宽高是把默认300*150的画布
      进行拉伸)  
     步骤:
       一、获取画布
           var huabu=document.getElementById("画布ID");
       二、获取环境
           var cxt=huabu.getContext("2d");

       三、画布API

           设置笔触的颜色
           cxt.strokeStyle="red";
           设置填充颜色
           cxt.fillStyle="red";

           设置笔触的宽度
           cxt.lineWidth=10;

           下笔
           cxt.beginPath();

           收笔
           cxt.closePath();

           设置起点
           cxt.moveTo(x,y);
           设置终点
           cxt.lineTo(x,y);

           执行画线
           cxt.stroke();
           执行填充
           cxt.fill();
           
           设置字体
           cxt.font="1px 字体";
           cxt.strokeText("需要的子",x,y);
           cxt.fillText("需要的子",x,y);

           渐变(设置fillStyle填充颜色为渐变色)
           var grd=cxt.createLinearGradient(0,0,579,80);
           grd.addColorStop(0,"#FF0000");
           grd.addColorStop(0.5,"#0000FF");
           grd.addColorStop(1,"#00FF00");
           cxt.fillStyle=grd;
           cxt.fillRect(0,0,500,500);

           画圆
           ctx.arc(x,y,r,开始位置,画多少弧度);
           ctx.arc(250,250,210,0,360*Math.PI/180);
           ctx.arc(250,250,210,0,2*Math.PI);

           在类似for循环环境下应使用
           ctx.save() 保存当前环境的状态
           ctx.estore() 返回之前保存过的路径状态和属性

           定时器清除画布(一般反正定时器那个函数的第一行)
           ctx.clearRect(x,y,w,h);
----------------------------------------------------
【css3】
1、边框

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

 2、影：

   (1)阴影:box-shadow:水平方向 垂直方向 模糊程度px表示 扩展值 颜色  inset(设置阴影为内阴影)
        不兼容的浏览器用法:-webkit（各浏览器内核前缀）-box-shadow: ;放在标准的上面(如果在js中设置 用boxShadow表示)
        设置多种颜色:设置多次，每次用逗号隔开，通过扩展值得不同来显示多种颜色。
    
    (2) 倒影:box-reflect:none 或 位置 偏移(本身与倒影的距离) 水印图片或渐变;(偏移和水印图片可有可无)
        不兼容的浏览器用法:-webkit（各浏览器前缀）-box-reflect: ;放在标准的上面
        位置的属性:above(上) below(下) left(左) right(右)
        偏移： 用长度值来定义倒影与对象之间的间隔。可以为负值
        水印图片: 设置倒影使用的图片或者渐变，默认为原内容
        注意:该属性目前仅webkit内核浏览器(chrome/safari/猎豹等)支持

        box-reflect：none | <direction> <offset>? <mask-box-image>?
        <direction> = above | below | left | right
        <offset> = <length> | <percentage>
        <mask-box-image> = none | <url> | <linear-gradient> | <radial-gradient> | <repeating-linear-gradient> | <repeating-radial-gradient>
        默认值：none
        取值：
        none：
        无倒影
        <direction>
        above：
        指定倒影在对象的上边
        below：
        指定倒影在对象的下边
        left：
        指定倒影在对象的左边
        right：
        指定倒影在对象的右边
        <offset>
        <length>：
        用长度值来定义倒影与对象之间的间隔。可以为负值
        <percentage>：
        用百分比来定义倒影与对象之间的间隔。可以为负值
        <mask-box-image>
        none：
        无遮罩图像
        <url>：
        使用绝对或相对地址指定遮罩图像。
        <linear-gradient>：
        使用线性渐变创建遮罩图像。
        <radial-gradient>：
        使用径向(放射性)渐变创建遮罩图像。
        <repeating-linear-gradient>：
        使用重复的线性渐变创建背遮罩像。
        <repeating-radial-gradient>：
        使用重复的径向(放射性)渐变创建遮罩图像。

    (3) 渐变:linear-gradient

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

  4、文本
  css3的文本阴影
  text-shadow:水平 垂直 模糊程度 颜色;
  css3的自动换行(不是单词间的换行 是折断非常长的单词)
  word-wrap:break-word;

  css3文本字体(慎用 字体不能太大 ie9只认识eot格式字体)
  用法:
  1、在样式中定义规则 再调用规则
  <style>
    @font-face{
        font-family:name; //定义规则名为name;
        src:url(字体路径.ttf),url(字体路径.eot); 
    }
    div{
        font-family:name;
    }
  </style>

  5、平面或2D
  元素转换的属性:transform 将元素页面坐标轴化
  通过 -webkit-transform:来实现兼容 谷歌等
         -ms-                       IE9
        -moz-                       火狐
          -o-                       open
  translate()   移动 transform:translate(xpx,ypx); 向左移动xpx,右ypx;
  rotate()      旋转  ; deg是度的css3写法(z轴为轴心)
  转了坐标轴

  scale()       缩放 transform:scale(宽倍数,高倍数) 缩放对象
  改变坐标轴的刻度

  skew()        翻转 transform:skwe(y轴向左便宜多少deg,x轴向下偏多少deg) 
  matrix(a,b,c,d,e,f);  
  a:x轴缩放
  d:y轴缩放
  b:y轴旋转的毒素(填cos旋转的度数值)          
  c:x轴旋转的毒素(填cos旋转的度数值)
  e:水平位移
  f:垂直位移    

  6、3D
  rotateX(deg);   沿着x轴旋转
  rotateY(deg);   沿着x轴旋转

  7、过渡(transition)   
  在原对象样式中 transition:属性1 时间,属性2 时间,..,属性n 时间;

  8、动画
  <style>
     @keyframes 规则名{
      from{height:0px;}
      to{height:100px;}
      ||
      0%{height:0px;}
      50%{height:50px;}
      100%{、、、}
     }
     div{

       animation: name duration timing-function delay iteration-count direction;(一次性写法)

       animation-name:规则名;  //绑定的规则名称
       animation-duration:2s;  //动画执行的时间
       animation-timing-function:...;//运动轨迹(匀速、变速等)
       animation-delay:1s;//定时执行
       animation-iteration-count:5||infinite(无限制);//指定动画只执行五次
     }
  </style>










