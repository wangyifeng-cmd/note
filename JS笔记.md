 

# JS笔记

### js组成部分

1.ECMAscript：语法规范 定义变量
2.DOM Document Object Model 文档对象模型
3.BOM Browser Object Model 浏览器对象模型

### 注释

```js
*/ 多行 /* 
//alt + shift + a
```



### 变量交换

```js
var w1 = 10;
var w2 = 20;
w1 = w1 + w2;
w2 = w1 - w2;
w1 = w1 - w2;
console.log(w1,w2);
```

### 获取数据变量

```js
typeof num
typeof (num)
```

### 五个数据类型

```js
number,string,boolean,null,underfined
```

### null因为历史遗留问题，为特殊数据object

```js
var nll = null;
console.log(typeof nll);
```

### 面试题1：NaN    (not  a  number不是个数字)

```js
var num;
console.log(num);//undefined
console.log(num + 10);//NaN
```

### 面试题2：不要拿小数相加，不要用小数验证小数

```js
var x = 0.1;
var y = 0.2;
var sum = x + y;
console.log(sum);//0.30000000000000004
console.log(sum == 0.3);//false
```

### 面试题3：不要用NaN验证是否是不是NaN

```js
var age;
console.log(age + 10 == NaN);//false
```

### 如何验证NaN   isNaN() ：是不是不是一个数字

```js
var num;
console.log(isNaN(num));//true
```

### 复制光标这行到下一行快捷键

```js
alt + shift + 向下键
```

### 比较常用的转义字符 \t ,\n,\\",\\'

```js
\t:tab键
\n:换行
\:想打"或'时
```

### 隐式转换 - * / %

```js
var age1 = 10;
var age2 = "5";
console.log(age1 - age2);//5
console.log(age1 * age2);//50
console.log(age1 / age2);//2
console.log(age1 % age2);//0
```



### 类型的颜色

```js
字符串-黑色  数字和布尔-蓝色  null和undefined-黑色
```



### parseInt()---转换为整数，从左往右转换，如果遇到字母立马停止转换

```js
console.log("fddv10bacfdsv");//fddv10bacfdsv
console.log(parseInt("fddv10bacfdsv"));//NaN
console.log(parseInt("10fddvbacfdsv"));//10
console.log(parseInt("10.98fddvbacfdsv"));//10
```

### parseFloat()---转换为小数

```js
console.log("fddv10bacfdsv");//fddv10bacfdsv
console.log(parseFloat("fddv10bacfdsv"));//NaN
console.log(parseFloat("10fddvbacfdsv"));//10
console.log(parseFloat("10.98fddvbacfdsv"));//10.98
```

### Number()---判断是否为数字，再输出

```js
console.log("fddv10bacfdsv");//fddv10bacfdsv
console.log(Number("fddv10bacfdsv"));//NaN
console.log(Number("10fddvbacfdsv"));//NaN
console.log(Number("10.98fddvbacfdsv"));//NaN
console.log(Number("10.98"));//10.98
```

### .toString---转为字符串

```js
var num = 10;
console.log(num);//蓝色的10
console.log(num.toString);//黑色的10
```

```js
var nll = null;
console.log(num.toString);//报错，无法转换
```

```js
var un;//undefined
console.log(num.toString);//报错，无法转换
```

### String()---转换为字符串，特殊作用为可以转换null和undefined

```js
var nll = null;
console.log(String(num));//null
```

```js
var un;//undefined
console.log(String(num));//undefined
```

### Boolean()---结果就两种，要么true，要么false，为false的只有五种可能：0，null，undefined，“”，NaN

```js
var str = "小明"；
var num = 18;
var nll = null;
var aa;
console.log(Boolean(str));//true
console.log(Boolean(num));//ture
console.log(Boolean(null));//false
console.log(Boolean(aa));//false
console.log(Boolean(1));//ture
console.log(Boolean(0));//false
console.log(Boolean(-1));//ture
```

### 字符类型加上正和负会自动转换为数值类型，如果字符类型中有不是数字的字符，会返回NaN

```js
var str = "18";
console.log(+str);//蓝色的18
console.log(-str);//蓝色的-18

var str1 = "18abc";
console.log(+str);//NaN
console.log(-str);//NaN

console.log(str - 0);//18
console.log(str1 - 0);//NaN
console.log(str + 0);//18abc0
```

### 弹窗输入

```js
var age = prompt("请输入您的年龄");
```

### 三元运算符

```js
var age = 18;
var result = age >= 18 ? "成年了" : "未成年";
console.log(result);//成年了
```

### switch~case（判断一个值的时候用）

```js
var num = parseInt(prompt("输入数字"))
switch (num) {
    case "1":
        console.log("星期一");
        break;
    case "2":
        console.log("星期二");
        break;
    case "3":
        console.log("星期三");
        break;
    case "4":
        console.log("星期四");
        break;
    case "5":
        console.log("星期五");
        break;
    case "6":
        console.log("星期六");
        break;
    case "7":
        console.log("星期日");
        break;
    default:
        console.log("你输入的超出范围了喔");
        break;
}
```

### 输出在界面，用js写入运行后的界面

```js
document.write("我好帅");
```

### break和continue

```js
break;//直接终止循环
continue;//直接跳出此次循环，跳到下一次循环
```

### 反转数组，数组名不能为name，原因是name特殊，在赋值的时候浏览器强制转成了string。

```js
var array = [1, 2, 3, 4, 5, 6, 7, 8, 9];
for (var i = 0; i <= array.length / 2; i++) {
    var temp = array[array.length - 1 - i];
    array[array.length - 1 - i] = array[i];
    array[i] = temp;
}
console.log(array);
```

### 函数

```js
function fun(形参) {
    var sum = x + y;
    return sum;
}
var result = fun(实参);
console.log(result + 39);
```

## 实参和形参个数不一致

### 第一种情况，实参大于形参，多的实参不调用

```js
function Sum(x, y) {
    return x + y;
}
console.log(Sum(10, 20, 30));//30
```

### 第二种情况，形参大于实参，多的形参没有赋值=undifined，数字 + undifined = NaN

```js
function Sum1(x, y, z) {
    return x + y + z;
}
console.log(Sum1(10, 10));//NaN
```

### 如果函数没有返回值，默认返回undifined

```js
function fun1(x, y) {
    var result = x + y;
}
console.log(fun1(1, 2));//undifined
```

### 如果函数有返回值return，默认一样返回undifined

```js
function fun2(x, y) {
    var result = x + y;
    return;
}
console.log(fun2(1, 2));//undifined
```

### return后面的值都不会执行

```js
function getsum(x,y){
     return x + y;
     console.log("我好帅");
}
console.log(getsum(10,20));
```

### 用圆周率PI求圆的面积

```js
function C(r) {
    return Math.PI * r * r;
}
console.log(C(10));
```

### 匿名函数

```js
var f = function (){
     console.log("f相当于一个函数名字");
}
f();
```

### 函数自调用

```js
(function(){
  console.log("函数自调用")
 })()
```

### 伪元素（不需要形参了，优化代码）伪数组

```js
function fun1() {
    var sum = 0;
    for (let i = 0; i < arguments.length; i++) {
        sum += arguments[i];
    }
    return sum;
}
console.log(fun1(10, 20, 30, 40));
```

### 判断是否是闰年

```js
function fun(){
     return year % 4 == 0 && year % 100 != 0 || year % 400 == 0;
}
```

### 斐波那契数列，一年有多少个兔子

```js
var num1 = 1;
var num2 = 1;
var sum = 0;
for (var i = 3; i <= 12; i++) {
    sum = num1 + num2;
    num1 = num2;
    num2 = sum;
}
console.log(sum);
```

### 全局变量中this指向window

```js
console.log(this);//window
```

### 普通函数里面this指向window

```js
function fun() {
    console.log(this);
}
fun();//window
```

### 变量提升，当网页一打开，首先浏览器会先遍历一遍代码，浏览器会把带var和function 提前声明

```js
//第一，如果是var浏览器会先提前声明 var age；只声明，不去赋值，默认的结果underfined
//第二，变量提升，只提升等号左边的，不会提升等号后面的
//第三，如果是function会声明加定义，会把整个function函数提升到代码前面
```

```js
//变量提升-示例1
console.log(a);//undefined
var a = 123;
console.log(a);//123
function f(){
     console.log(a);undefined
     var a = 456;
     console.log(a);//456
}
f();
console.log(a);

//伪代码
var a;
a = 123;
console.log(a);//123
function f(){
     var a;
     console.log(a);//undefined
     a = 456;
     console.log(a);//456
}
f();
console.log(a);//123

//示例二
var foo = 1;
function fun(){
     if(!foo){
          var foo = 10;
     }
     console.log(foo);//10
}
fun();

//伪函数
var foo = 1;
function fun(){
     var foo;
     if(!foo){
          foo = 10j;
     }
     console.log(foo);//10
}
fun();

//示例三
console.log(a,b,c);//undefined undefined undefined
var a = 10,b = 20, c = 30;
function fun(a){
     console.log(a,b,c);//10 undefined 30
     var b = a = c =100;
     console.log(a,b,c);//100 100 100
}
fun(10,20);
console.log(a,b,c);//10 20 100

//伪代码
var a;
var b;
var c;
console.log(a,b,c);//undefined undefined undefined
var a = 10,b = 20, c = 30;
function fun(a){
     var b;
     console.log(a,b,c);//10 undefined 30
     b = a = c = 100;
     console.log(a,b,c);//100 100 100
}
fun(10,20);
console.log(a,b,c);//10 20 100
```

### 内置对象一

```js
//内置对象（系统自带的），后面会学习浏览器对象BOM，自定义构造函数对象（new一下就会有对象了---面向对象里面会详细讲解）
//内置对象：Math，Date，Arr，String···
Math.PI//派
Math.max()//最大值
Math.min()//最小值
Math.abs()//绝对值
Math.random()//随机获取 0 到 1 之间的随机数，[0,1)
Math.ceil(12.5)//13   向上取整
Math.floor(12.5)//12   向下取整
Math.pow(2,4)//16   求知数次幂
Math.sqrt(16)//4   求平方根
Math.round(10.98)//11   小数四舍五入
```

### 随机点名

```js
var names = ["wyf","zwh","myl","hjh"];
console.log(names[parseInt(Math.random() * names.length)]);
```

### 内置对象二

```js
function da(dt) {
    var y = dt.getFullYear(); //获取年
    var m = dt.getMonth() + 1; //我们的月是从0开始的，所以要加1
    var d = dt.getDate(); //获取日期
    var h = dt.getHours(); //获取小时
    var min = dt.getMinutes(); //获取分钟
    var sec = dt.getSeconds(); //获取秒
    var week = dt.getDay(); //获取星期几
    switch (week) {
        case 1:
            week = "星期一";
            break;
        case 2:
            week = "星期二";
            break;
        case 3:
            week = "星期三";
            break;
        case 4:
            week = "星期四";
            break;
        case 5:
            week = "星期五";
            break;
        case 6:
            week = "星期六";
            break;
        case 0:
            week = "星期天";
            break;
    }
    m = m < 10 ? "0" + m : m;
    d = d < 10 ? "0" + d : d;
    h = h < 10 ? "0" + h : h;
    min = min < 10 ? "0" + min : min;
    sec = sec < 10 ? "0" + sec : sec;
    return y + "年" + m + "月" + d + "日" + h + "小时" +
        min + "分钟" + sec + "秒" + week;
}
var dt = new Date(); //获取系统日期
console.log(da(dt));

```

### 随机取颜色 #xxxxxx

```js
function getColor() {
    var str = "#";
    var arr = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f", "g"];
    for (let i = 0; i < 6; i++) {
        str += arr[parseInt(Math.random() * arr.length)];
    }
    return str;
}
console.log(getColor());
```

### 当页面加载时运行---入口函数

```js
window.onload = function() {
}
```

```js
//获取id改div的背景颜色
window.onload = function() { document.getElementById("color").style.backgroundColor = getColor();//利用
}
```

```js
document --- 文档
get --- 获取
Element --- 元素
By --- 通过
Id --- 页面的id
```

### 获取数组索引的值  .chatAt()

```js
var str = "wyfhaoshuai";
console.log(str.chatAt(10));
```

### 内置对象二

```js
//.charAt();获取索引所在位置的字符
var str = "fjdksovhwiorfvsioajdfiosghviowjfidopafjpioqafjw"
console.log(str.charAt(11));

//.String.fromCharCode()获取ascll码中对应的值
var word = String.fromCharCode(65, 66, 67);
console.log(word);
var sos = String.fromCharCode(83, 79, 83);
console.log(sos);

//.concat()返回拼接之后的字符串
var str5 = "我们";
var str6 = str5.concat("wyf", "hao", "shuai");
console.log(str6); //我们wyfhaoshuai

//.indexOf("想找的字符串"，送哪里开始找)  返回想找的字符串的索引  
var str10 = "不是吧你别在这里吵了";
var index = str10.indexOf("吵", 8);
console.log(index); //8

//.lastIndexOf("想找的字符串")  返回想找的字符串的最后一个的索引
var str10 = "不是吵吧你别在这里吵了";
var index = str10.lastIndexOf("吵");
console.log(index); //9

//.replace("替换目标"，"替换对象")  替换字符串
var str11 = "wyf好帅，是一个靓仔";
str12 = str11.replace("帅", "靓");
console.log(str12); //wyf好靓，是一个靓仔

//.slice(开始的索引值，结束的索引值（不包括）)提取两个索引之间的字符
var str13 = "你开玩笑是吧不要这样";
var str14 = str13.slice(4, 7);
var str15 = str13.slice(4); //把剩下的所有都提取
console.log(str14);

//.splice(n,m,x,y,z)  把数组从索引n开始删除m个元素，用x,y,z代替删除的m项，返回值是被删的数组，原来的数组已经改变(备注：增删改除)
var str22 = [1, 2, 3, 4, 5, 6];
var str23 = str22.splice(2, 2, 7, 8, 9);
console.log(str23);//3,4
console.log(str22);//1,2,7,8,9,5,6
//扩展1，当m是0的时候，他是把x,y,z..添加到索引n的前面
var str24 = [1, 2, 3, 4, 5, 6];
var str25 = str24.splice(2, 0, 7, 8, 9);
console.log(str24);//1,2,7,8,9,3,4,5,6
//扩展2，没有xyz，相当于直接删除m项
var str26 = [1, 2, 3, 4, 5, 6];
var str27 = str26.splice(2, 2);
console.log(str26);//1,2,5,6
//扩展3，当什么都没写，返回空数组
var str30 = [1, 2, 3, 4, 5, 6];
var str31 = str30.splice();
console.log(str31);//[]
console.log(str30);//1,2,3,4,5,6
//扩展3，当.splice(0)是，相当于删除整个数组
var str28 = [1, 2, 3, 4, 5, 6];
var str29 = str28.splice(0);
console.log(str29);//1,2,3,4,5,6
console.log(str28);//[]

//.split("22","拆分后留下的字符串个数")  以规定字符拆分字符串形成数组
var str16 = "w|y|f|h|a|o";
var str17 = str16.split("|");
console.log(str17); //["w", "y", "f", "h", "a", "o"]

//.substr("开始位置","截取个数")   返回截取后的字符，个数可以省略
var str18 = "我们都是靓仔，靓妹";
var str19 = str18.substr(4, 2);
console.log(str19);//靓仔

//.substring("开始位置","结束的位置（不包含）")  返回截取后的字符
var str20 = "我们都是靓仔，靓妹";
var str21 = str20.substring(4, 6);
console.log(str21);//靓仔

//.toLocaleLowerCase()  转换成小写字母
//.toLowerCase()  转换成小写字母
var str1 = "LIVE ME";
console.log(str1.toLocaleLowerCase());
console.log(str1.toLowerCase());

//.toLocaleUpperCase()  转换成大写字母
//.toLowerCase()  转换成大写字母
var str2 = "live me";
console.log(str2.toLocaleUpperCase());
console.log(str2.toUpperCase());

//.trim()  删除两端的空格，中间的空格删不了
var str3 = "   张文瀚  傻逼   "
console.log(str3.trim());
```

### 作业

```js
//找其中的字符串
var str4 = "张文瀚unglyfulishstupid";
var index = str4.indexOf("张文瀚");
console.log(index);//0
console.log(str4.substr(index, 3));//张文瀚

//找字符串中所有想找到字符的index
var str5 = "jhkgfldsjghdlsjghdlsjghdlslfjkghdksjfhg";
var index1 = 0;
var key = "j";
while ((index1 = str5.indexOf(key, index1)) != -1) {
    console.log(index1);
    index1 += key.length;
}
```

### 数组

```js
//第一种
var arr1 = [1,2,3,4,5];
//第二种--内置构造函数方式new来创建
var arr2 = new Array(1,2,3,4,5);

//第一种和第二种的区别
var arr3 = [6];
console.log(arr1.length);//1
var arr4 = new Array(6);//创建对象，只写一个数字在，就表示有这么多个数字的空字符
console.log(arr4.length);//6
console.log(arr4);//empty*6
```

### 判断数组的方式

```js
// instanceof 判断这个对象是否是数组，如果是为ture，如果不是为false
var arr1 = [];
console.log(arr1 instanceof array);//ture
var arr2 = 10;
console.log(arr2 instanceof array);//false

// isArray
var arr3 = [];
console.log(Array.isArray(arr3));//ture
```

### 内置对象三

```js
//.push(值1，值2...)  给数组后面添加元素，返回值为数组的长度
var arr1 = [1,2,3,4,5];
var result1 = arr1.push(100,200);
console.log(result1,arr1);//1,2,3,4,5,100,200

//.unshift(值1，值2...)  给数组前面添加元素
var arr2 = [1,2,3,4,5];
var result2 = arr2.unshift(100,200);
console.log(result2,arr2);//100,200,1,2,3,4,5

//.pop()  删除数组的最后一项，返回值是删除的那一项
var arr3 = [1,2,3,4,5];
var result3 = arr3.pop();
console.log(result3,arr3);//1,2,3,4

//.shift()  删除数组的第一项，返回值是删除的那一项
var arr4 = [1,2,3,4,5];
var result4 = arr4.shift();
console.log(result4,arr4);//2,3,4,5

//.reverse()  数组反转
var arr5 = [1,2,3,4,5];
var result5 = arr5.reverse();
console.log(result5);//5,4,3,2,1

//.sort()  数组排序，只能排序10以内的数字
var arr6 = [3,6,3,7,8,1,2];
var result6 = arr6.sort();
console.log(result6);//1, 2, 3, 3, 6, 7, 8

//.sort(dunction(a,b){a - b})  数字如果超过10，用“回调函数”，如果是b-a就是从大到小
var arr7 = [1,100,232,45,65,4,87];
var result7 = arr7.sort(function(a,b){
     return a - b;
})//1, 4, 45, 65, 87, 100, 232
```

## DOM Document Object Model 文档对象模型

### 入口函数：<u>单独  js  文件</u>   或   <u>script在body上面</u>    对文档处理需要加载页面

```js
window.onload = function() {
    //文档处理内容
}
```

### 鼠标事件

```js
onclick//单击
ondblclick//双击
onmouseover//经过
onmouseout//离开
```

### 改img的图片 ，动作在控件里面

```html
<img src = "./图片2.jpg" id="i"></img>
<button onclick = "img()"></button>//

```

```js
function img(){
     document.getElementById("i").src("./图片1.jpg");
}
```

### 动作在js里

```html
<button class="d" id="btn"></button>
```

```js
window.onload = function() {
    var btn = document.getElementById("btn");
    btn.onclick = function() {//
        alert("好啊");
    }
}
```

###   获取text的内容

```js
p.innerText = "好啊";
```

### 获取多个相同标签，把这多个标签变成集合（伪数组）（例子为p标签）

```js
var pObjs = document.getElementsByTagName("p");
console.log(pObjs);//p, p, p, p, p, p
for (var i = 0; i < pObjs.length; i++) {
    pObjs[i].innerText = "傻了吧";
}
```

### 修改a标签的href

```js
var aObj = document.getElementById("a");
aObj.href = "https://app.mockplus.cn/team/pwajjstnyc";
```

### 隐藏和显示图片

```html
<div>
     <input type="button" value="隐藏" id="dis1">
     <input type="button" value="显示" id="dis2">
</div>
<div id="i">
     <img src="./pic/光.jpg" alt="" id="img">
</div>
```

```js
var dis1 = document.getElementById("dis1");
var dis2 = document.getElementById("dis2");
var i = document.getElementById("i");
dis1.onclick = function() {
     i.style.display = "none";//隐藏
}
dis2.onclick = function() {
     i.style.display = "block";//显示
}
```

### public公用调用函数--my$()

```js
//独立设一个公用js文件
function my$(id){
    	return document.getElementById(id);
}
```

```js
//在独立js文件中调用
my$("html中的id");
```

### 调用<img>的width和height的数据不用加px

```js
wyf$("img").width = "200";
```

### this的用法1

```html
<img src="./pic/昼夜1.jpg" alt="" id="night">
```

```js
wyf$("night").onmouseover = function() {
     this.src = "./pic/昼夜2.jpg";
}
wyf$("night").onmouseout = function() {
     this.src = "./pic/昼夜1.jpg";
}
```

### 排他思想

```html
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
```

```js
var bObjs = document.getElementsByTagName("input");
    for (var i = 0; i < bObjs.length; i++) {
        bObjs[i].onclick = function() { //获取每个按钮点击事件
            for (let j = 0; j < bObjs.length; j++) { //第一件事情
                bObjs[j].value = "叼啊"; //把每个按钮的值改为相同的值
            }
            this.value = "菜啊"; //第二件事情，把自己变单独的值
        }
    }
```

### 改变性别，用checked为true判定

```html
<input type="button" value="女的" id="n">
<input type="radio" name="nex" id="nan">男
<input type="radio" name="nex" id="nv">女
```

```js
wyf$("n").onclick = function() {
     wyf$("nv").checked = "fjdskfjsdko";//true就是被选中
}
```

### 下拉选择菜单，用selected为true判定

```html
<input type="button" value="王译锋喜欢吃的" id="wyf">
<select name="吃的" id="">
     <option value="牛腩粉">牛腩粉</option>
     <option value="海七沙县炒面">海七沙县炒面</option>
     <option value="红茶玛奇朵" id="hong" >红茶玛奇朵</option>
     <option value="培根">培根</option>
     <option value="ei">ei</option>
</select>
```

```js
wyf$("wyf").onclick = function() {
     wyf$("hong").selected = true;
}
```

### 点击改变样式，背景宽度长度。。

```js
this.style.width = "100px";
this.style.backgroundColor = "skyblue";
```

### 同一个按键控制隐藏和显示

- 优化之前

```html
<input type="button" value="隐藏" id="btn3">
<img src="./pic/抠肉肚脐3.jpg" alt="" width="200" id="im1">
```

```js
wyf$("btn3").onclick = function() {
     if (this.value == "隐藏") {
          wyf$("im1").style.display = "none";
          this.value = "显示";
     } else {
          wyf$("im1").style.display = "inline-block";
          this.value = "隐藏";
     }
}
```

- 优化之后

```css
.dis_none {
     display: none;
}
```

```html
<input type="button" value="优化后的隐藏" id="better">
<div id="clss">优化后隐藏显示的内容</div>
```

```js
wyf$("better").onclick = function() {
     if (wyf$("clss").className != "dis_none") {
          wyf$("clss").className = "dis_none";
          this.value = "优化后的显示";
     } else {
          wyf$("clss").className = "";
          this.value = "优化后的隐藏";
     }
}
```

### .className用 js 添加 css 样式

```css
.cls {
     width: 100px;
     height: 100px;
     background-color: rgb(0, 153, 255);
}
```

```html
<div id="sty">.classname</div>
```

```js
wyf$("sty").className = "cls";
```

### 用三元运算开关灯，夜晚模式和白天模式

```html
<input type="button" value="开/关灯" id="light">
```

```js
wyf$("light").onclick = function() {
     document.body.style.backgroundColor = document.body.style.backgroundColor != "black" ? "black" : "";
}
```

### 获取body

```js
document.body.style.backgroundColor;
```

### 按按钮禁止填写文本框

```html
<input type="button" value="禁止你写字" id="stop">
<input type="text" name="" id="text">
```

```js
wyf$("stop").onclick = function() {
     wyf$("text").disabled = "true";
}
```

### 让a标签无法跳转return false

- 第一种方法，行内解决

```html
<a href="https://www.hanjutv2020.com/" id = "a" onclick="alert('哎呀  你电我干嘛'); return false">让a标签无法跳转</a>
```

- 第二种方法，js解决

```js
wyf$("a").onclick = function() {
     return false;
}
```

### 美女相册(头像)

```html
<ul id="l">
     <li>
          <a href="./pic/头像2.jpeg"><img width="100" src="./pic/头像2.jpeg" alt=""></a>
     </li>
     <li>
          <a href="./pic/头像16.jpeg"><img width="100" src="./pic/头像16.jpeg" alt=""></a>
     </li>
     <li>
          <a href="./pic/头像15.jpeg"><img width="100" src="./pic/头像15.jpeg" alt=""></a>
     </li>
     <li>
          <a href="./pic/头像14.jpeg"><img width="100" src="./pic/头像14.jpeg" alt=""></a>
     </li>
</ul>
<img src="./pic/头像20.jpeg" alt="" width="400" id="a1">
```

```js
var aObjs = document.getElementById("l").getElementsByTagName("a");
for (var i = 0; i < aObjs.length; i++) {
     aObjs[i].onclick = function() {
          wyf$("a1").src = this.href;
          return false;
     }
}
```

### 鼠标经过出现，鼠标离开消失（二维码）

```html
<div class="erweima">
     <a href="#"></a>
     <div class="nv hide" id="light">
          <img src="./pic/光.jpg" alt="" width="150">
     </div>
</div>
```

```js
var aObj = document.getElementsByTagName("a")[0];
aObj.onmouseover = function() {
     wyf$("light").className = "nv show";
}
aObj.onmouseout = function() {
     wyf$("light").className = "nv hide";
}
```

### getElementsByName获取相同name值形成集合（伪函数）

```html
<input type="button" value="别点击喔" id="name"><br>
<input type="text" value="不是吧！！！" name="name1"><br>
<input type="text" value="不是吧！！！" name="name2"><br>
<input type="text" value="不是吧！！！" name="name1"><br>
<input type="text" value="不是吧！！！" name="name3"><br>
<input type="text" value="不是吧！！！" name="name1"><br>
<input type="text" value="不是吧！！！" name="name1"><br>
```

```js
wyf$("name").onclick = function() {
     var inputs = document.getElementsByName("name1");
     for (var i = 0; i < inputs.length; i++) {
          inputs[i].value = "你真点啊";
     }
}
```

### querySelector和getElementById相似获取id，但是获取的id前要加#

### querySelectorAll和getElementByClassName相似获取class，但是获取的class前要加.

```html
<input type="button" value="别点击喔" id="name"><br>
<div id="hong"></div>
```

```js
var a = document.querySelector("#name");
a.onclick = function() {
     var d = document.querySelector("#hong");
     d.style.backgroundColor = "black";
}
```

### 获取元素的方式总结

- 根据  "id"  获取元素：document.getElementById("id的值")

- 根据  "标签"  获取元素：document.getElementsByTagNmae("标签的名字")

- 根据  "name的值"  获取元素：document.getElementsByName("name的值")

- 根据  "类样式(class)"  获取元素：document.getElementByClassName("类样式的名字")

- 根据  "选择器的方式"  获取元素：

  1.document.querySelector("#id")

  2.document.querySelector(".class")

- 获取  "body"  标签：document.body

### 获取焦点和失去焦点

```html
<input type="text" name="" class="t" id="t" value="你个傻逼">
```

```js
wyf$("t").onfocus = function() {
     if (this.value == "你个傻逼") {
          this.value = "";
          this.style.color = "black";
}
wyf$("t").onblur = function() {
     if (this.value == "") {
          this.value = "你个傻逼";
          this.style.color = "gray";
     }
}
```

### 自己添加属性，随便取名

- 添加属性：setAttribute("属性的名字","属性的值")
- 获取属性：getAttribute("属性的名字")

```html
<ul id="uu">
     <li>好嗨哟</li>
     <li>牛啊牛啊</li>
     <li>绣得天花乱坠</li>
     <li>抱歉</li>
     <li>不是吧</li>
</ul>
```

```js
var list = document.getElementsByTagName("li");
for (var i = 0; i < list.length; i++) {
     list[i].setAttribute("xswl", (i + 1) * 20);
     list[i].onclick = function() {
          alert(this.getAttribute("xswl"));
     }
}
```

###    删除标签的属性（包括系统自带的）

```html
<input type="button" value="删除标签属性" id="btn">
<div id="d" score="30" class="d"></div>
```

```js
wyf$("btn").onclick = function() {
     wyf$("d").removeAttribute("score");
     wyf$("d").removeAttribute("class");//系统自带的class
}
```

### 添加文本  innerText和innerHTML的区别

```html
<input type="button" value="点击增加inner" id="btn">
<div class="inner" id="inner"></div>
```

```js
wyf$("btn").onclick = function() {
     wyf$("inner").innerText = "牛啊牛啊";
     wyf$("inner").innerText = "<p>一碗化州牛腩粉 吃出男人的沉稳</p>"
     wyf$("inner").innerHTML = "牛啊牛啊";
     wyf$("inner").innerHTML = "<p>一碗化州牛腩粉 吃出男人的沉稳</p>";
}
```

### 导航栏，列表

```css
#hd {
     font-size: 0;
}

#hd span {
     display: inline-block;
     width: 50px;
     height: 30px;
     font-size: 16px;
     text-align: center;
     line-height: 30px;
}

#bd ul li {
     width: 200px;
     height: 200px;
     background-color: rgb(0, 255, 98);
}

.hide {
     display: none;
}

.show {
     display: inline-block;
}

.sele {
     background-color: rgb(255, 145, 0);
}
```

```html
<div>
     <div id="hd">
          <span class="sele">wyf1</span>
          <span>wyf2</span>
          <span>wyf3</span>
          <span>wyf4</span>
     </div>
     <div id="bd">
          <ul>
               <li class="show">1</li>
               <li>2</li>
               <li>3</li>
               <li>4</li>
          </ul>
     </div>
</div>
```

```js
var sp = document.getElementsByTagName("span");
var li = document.getElementsByTagName("li");
for (var i = 0; i < li.length; i++) {
     if (li[i].className != "show") {
          li[i].className = "hide";
     }
}
for (var i = 0; i < sp.length; i++) {
     sp[i].setAttribute("index", i);
     sp[i].onclick = function() {
          for (var j = 0; j < sp.length; j++) {
               sp[j].removeAttribute("class");
          }
          this.className = "sele";//上面导航栏的排他
          var num = this.getAttribute("index");
          for (var k = 0; k < li.length; k++) {
               li[k].className = "hide";
          }
          li[num].className = "show";//下面界面的排他
     }
}
```

### 出现Cannot set property 'className' of undefined的问题

> for (var i = 0; i < sp.length; i++) {
>      sp[i].setAttribute("index", i);
>      sp[i].onclick = function() {
>      li[i].className = "show";//这行出现问题
>      }
> }
>
> 由于这是事件过程，当鼠标移到元素上触发事件时，i的值早已不是当初声明事件过程时的那个i了，而是等于oLi.length（你用console.log把i的值输出一下就知道了），因此oLi[i]实际上就已经超出oLi的范围了，所以是undefined

