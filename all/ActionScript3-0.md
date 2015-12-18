title: "ActionScript3.0"
date: 2015-05-14 22:22:09
tags: 语言
---
#基础
##数据类型
1、as3的基元数据类型:Boolean、int、Number(可用存小数)、String、uint(颜色值 alpha一般用它存)
2、as3的复杂数据类型:Array、Date、Error、Function、RegExp、XML、XMLList和自定义类；
##变量
==变量必须先声明在使用
==as2中没加数据类型默认为object;
###变量的声明
var 变量名:数据类型;
var 变量名:数据类型=值;(值得类型必须跟对应的数据类型相同)
var 变量名; 这是正确的 默认类型为untyped(未声明类型)  和 var 变量名:*;效果相同
###变量的命名规则
1.尽量使用有含义的英文单词作为变量名
2.变量名采用骆驼式命名法
3.变量命名符合“min-length&&max-information”原则(太长的单词尽量缩写、不要太长)
4.尽量避免变量名中出现数字编号
###变量的本质
==变量持有引用（Reference），而引用则指向要操作的对象。因此，实际我们是通过引用来操作对象
==基元数据类型相当于值类型(该类型的对象是不变对象 所以不影响值)、复杂数据类型就是引用数据类型
==值类型一定不用new关键字的
==当“var b:Array=a;”这一句执行时，实际上是新创建了一个数组变量 b，将 a 持有的引用（而不是值）赋值给了 b。

var a:Array = new Array(1,2,3);
var b:Array = a;
b = new Array(4,5,6);    //新建一个数组[4,5,6]，将引用赋值给 b

这样两个引用是互不干扰的

在Java中基础数据类型不是对象，相对应的的包装了才是
在Actionscript3.0中基础数据类型就是对象
var i:int=1000; 就能直接 i.方法  设置功能了

##const声明常量

==这种特殊变量只能在声明时赋值，而且一经赋值，就不能再更改。
声明方法:const foo:int = 100;

正确:const foo:Array = [1,2];
     var b:Array = foo;
     b[1] = 100;

错误:foo = [2,3];

##基础数据类型(是常用的数据类型 并不是基元数据类型)

###基础数据类型的范围
包括:(1)所有的基元数据类型：Boolean、int、uint、Number、String。
    
     (2)两种复杂数据类型：Array、Object。

###基础数据类型的注意事项
####Boolean
As2.0中默认值是undefined*****在As3.0中默认值是false
####int、uint、Number
int:四个字节 正负个一办
uint:四个字节 都是正的
Number:六个字节 存小数(最好是除法或有小数点时使用)
####String
==默认值是null
==字符串的声明
var stringSample1:String;//声明一个 String 型变量。此时未定义，默认为null
var stringSample2:String = ""; //声明一个空的字符串，已经定义
var stringSample3:String = new String(); //用包装类来声明，与上行效果相同
var stringSample4:String = "abc"; //声明一个内容为 abc 的字符串
var stringSample5:String = new String("abc"); //同上行效果相同
var stringSample6:String = 'abc'; //也可以使用单引号来声明新字符串
==得到字符串长度:.length    trace();输出
==输出一些符号:使用/转义字符  
####Array
As3.0支持稀疏数组(中间某些元素可以空着)和非类型数组(不是所有元素都是同一种数据类型)
==数组的声明
 var a:Array; //声明一个数组变量 a，但还没有告诉 a 这个引用指向谁。trace 得到 null
 var b:Array = []; //直接声明一个空数组 b。trace 得到空白的显示，但不再是 null 了   
 var c:Array = new Array(); //效果同声明 b 的方法
 var d:Array = [1,2,3,4];       //直接使用[]操作符，建立一个含有整数 1、2、 3、4 的数组      
 var e:Array = new Array(1,2,3,4);//使用 Array 类来进行和 d 同样的操作
 var f:Array = new Array(5);//声明一个长度为 5 的空数组，此时每个数组元素都为空
#### Object 及关联数组

 Object 可以动态添加属性。看下例：
//先初始化，即新建一个空对象，将其引用赋值给变
Var kingda:Object = {};
//新增一个属性 name，将字符串“黑羽”赋值给它
kingda.name = "黑羽";
//新增一个属性 gender，将数字 1 赋值给它
kingda.gender = 1;
trace (kingda.name);
//输出：黑羽
  也可以动态添加方法，接上例：
kingda.hello = function(){
     trace("Hi,ActionScript 3")
}
kingda.hello();
//输出：Hi,ActionScript 3

访问对象成员时 . 符号和 [""]的效果一样
####多维数组
其实多维数组就是它的成员也是 Array（数组）。所以多维数组往往又被称为嵌套数组。

                          多维数组创建和访问
//直接使用中括号嵌套来创建多维数组
var sample1:Array = [[1,2,3],[4,5,6],[7,8,9]];
trace (sample1[2]);
//注意数组索引是从零开始的，所以输出的是第三个数组：7,8,9
trace (sample1[2][1]);
//输出第三个数组第二个元素:8
//使用构造函数来创建多维数组
var sample2:Array = new Array(new Array(1,2,3), new Array(4,5,6), new
Array(7,8,9));
trace (sample2[2][1]);
//输出：8
//先定义数组的长度，再一一添加子数组
var sample3:Array = new Array(3);
sample3[0] = [1,2,3];
sample3[1] = [4,5,6];
sample3[2] = [7,8,9];
trace (sample3[2][1]);
//输出：8
####各类型的默认值
var a:int, b:uint, c:Number; //int 型，默认值为：0 、 unit 型，默认值为：0、Number 型，默认值为：NaN
var d:String, e:Boolean;     //String 型，默认值为：null、Boolean 型，默认值为：false
var f:Array;                 //Array 型，默认值：null
var g:Object;                //Object 型，默认值为：null
var h;                       //未声明类型，默认值为：undefined
var i:*;                     //未声明类型，默认值为：undefined
####运算符之 typeof、is、as

typeof 是用字符串形式返回对象的类型。使用方法如下：
trace (typeof 10);   //输出：number

is与as的差别(正确:is输出true as输出该值 错误:is输出false as输出null)
is 和 as 运算符使用很广泛。 用来判断一个对象是否属于一种类型，返回is
布尔值，true 代表属于，false 表示不属于。使用格式如下：
trace (9 is Number);   //输出：true
 as 与 is 格式一致，内容不同：如果一个对象属于一种类型，那么 as 返回这
 个对象；否则返回 null。例子：
  trace (9 as Number);     //输出：9
  trace (9 as Array);  //输出：null
####   in
 in 关键字用来判断一个对象是否作为另一个对象的键（Key）或索引，存在
返回 true，不存在返回 false。见示例 2-4。
                          示例 2-4 运算符 in 的使用
  var a:Array = ["q","w","e"];
                          //数组 a 含有索引 2，所以为 true
  trace(2 in a);
                            //只有个元素，没有索引为 3 的元素，所以为 false
  trace(3 in a);
  var b:Object = {ary:a, name:"ok"};
                               //true，确实有 ary 为键的属性
  trace ("ary" in b);
  trace ("name" in b);        //同上
  import flash.utils.Dictionary;
  var c:Dictionary = new Dictionary();       //建立字典对象
                                                //把数组 a 作为键
  c[a] = "a value";
                                                //把对象 b 也作为键
  c[b] = "b value";
  trace (a in c);                              //输出 true
  trace (b in c);                                //输出 true
 ####delete
 它只可以来用删除对象的动态实例属性，非动态属性不能删除。
var b:Object = {ary:"one",name:"ok"};
deleted b;                  //会报错，不能这样删除了
deleted b.ary;              //成功，因为 ary 是 b 对象的动态属性
##循环
ActionScript支持的循环:while，do-while，for，for...in，for each...in
###for...in，for each...in
for...in 输出变量的值是属性,对应的以数组下标形式可以输出值(需要属性和值是使用)
for each...in 输出变量的值是值(只需要值时使用)

                     示例 3-2for…in 和 for each…in 的使用

        var kingdaBooks:Object = {flex_book:"Flex 3 殿堂之路",
                                     as_book:"ActionScript 3 殿堂之路",
                                     Apollo_book:"Apollo 殿堂之路"};
        for (var k in kingdaBooks) {
                           trace ("成员名字(键):"+k+"\t 成员(值)"+k]);
        }
        /*输出：
        成员名字(键):as_book               成员(值):ActionScript 3 殿堂之路
        成员名字(键):Apollo_book       成员(值):Apollo 殿堂之路
        成员名字(键):flex_book           成员(值):Flex 3 殿堂之路
        *
        for each (var k in kingdaBooks) {
             trace ("成员:"+k);
        }
        /*
        成员:ActionScript 3 殿堂之路
        成员:Apollo 殿堂之路
        成员:Flex 3 殿堂之路
        */
###break和continue
break:直接跳出循环
continue:跳出本次循环(函数中效果和return一致)
####使用label方法跳出多重循环
         示例 3-3 使用 break 和 continue 的标签用法来控制嵌套循环

var i:int = -1;
parent: //本行设定最外层循环标签为 parent
do {
     trace("{父循环");
     son: //本行设定第二层循环标签为：son
     while(true) {
           i++;
           trace("\t{子循环:i = "+i);
           for (var k:int = 0; k<3; k++) {
           trace ("\t\t{孙循环:k=" +k);
           if(i==1 ) {
                 trace("\t\ti==1:continue 孙循环");
                 continue;
           }
           if(i==2) {
                 trace("\t\ti==2:continue 子循环:son");
           }
           if(i==3) {
                 trace("\t\ti==3:continue 父循环:parent");
                 continue parent;
           }
           if (i==4) {
                 trace("\t\ti==4:break 孙循环");
                 break;
           }
           if (i==5) {
                 trace("\t\ti==5:break 子循环:son");
                 
           }
           if (i==6) {
                 trace("\t\ti==6:break 父循环:parent");
                 break parent;
           }
           trace("\t\t 孙循环}");
      }
      trace ("\t 子循环");
    }
         trace("父循环}");
    }while(true);

##函数
函数的定义:
(1)函数语句定义法(编译时会被提升 可以在之前调用)
格式:function 函数名{参数1:参数类型,参数2:参数类型}:返回值类型{函数体}
例子:function teseAdd(a:int,b:int):int{ return a+b;}
(2)函数表示式定义法(必须先先定义才能使用 调用一定要在定义之后才行)
格式:var 函数名:Function=function(参数1:参数类型,参数2:参数类型,参数3:参数类型):返回值类型{函数体}
例子:var testAdd:Function = function(a:int,b:int):int {return a+b;}

两者的区别
1、上述的调用
2、this:函数语句定义的this固定在一个定义域上 ，而表示定义的this随着附着的对象不同，所代表的也变了


















                                         







