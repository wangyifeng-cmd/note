 

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

### 函数自调用（函数自己调用自己）

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
var bObjsarray = Array.from(bObjs);//可以把集合转化为真正的数组，这里没用到
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

### 获取焦点和失去焦点（锚点）

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

### 导航栏，tab栏

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

## 节点的介绍

### 必须要熟练---倒背如流

> nodeType：节点类型（1代表的标签节点，2代表的是属性节点，3代表的是文本节点）
>
> nodeName：节点名字（如果是标签节点---获取到的是大写的标签名；如果是属性节点--- 获取到的是小写的属性名；文本节点---获取的是#text）
>
> nodeValue：节点的值（如果是标签节点---null，属性节点---属性的值，文本节点---文本内容）
>
> |          | nodeType |   nodeName   | nodeValue |
> | :------: | :------: | :----------: | :-------: |
> | 标签节点 |    1     | 大写的标签名 |   null    |
> | 属性节点 |    2     | 小写的属性名 | 属性的值  |
> | 文本节点 |    3     |    #text     | 文本内容  |
>
> 

> #### 对比记忆法
>
> DOM节点          HTML文档
>
> 元素节点               标签
>
> 属性节点               属性
>
> 文本节点            文本内容
>
> 注释节点               注释

### 获取父级节点   <重点一>

```js
console.log(uu.parentNode);
```

### 获取父级元素   <重点二>

```js
console.log(uu.parentElement);
```

### 获取子级节点（多个）   <重点三>

```js
console.log(dd.childNodes);
```

### 获取子级元素   <重点四>

```js
console.log(dd.children);
```

- 以上四种所有浏览器都支持

### 获取子级第一个子节点

```js
console.log(dd.firstChild);//IE8中是第一个子元素
```

### 获取子代第一个子元素

```js
console.log(dd.firstElementChild);//IE8不支持
```

### 获取最后一个子节点

```js
console.log(ll.lastChild);//IE8中是最后一个子元素
```

### 获取最后一个子元素

```js
console.log(ll.lastElementChild);//IE8不支持
```

### 获取前一个兄弟节点

```js
console.log(ll.previousSibling);//IE8中是前一个兄弟元素
```

### 获取前一个兄弟元素

```js
console.log(ll.previousElementSibling)//IE8不支持
```

### 获取下一个兄弟节点

```js
console.log(ll.nextSibling);//IE8中是下一个兄弟元素
```

### 获取下一个兄弟元素

```js
console.log(ll.nextElementSibling);//IE8不支持
```

### 筛选节点

```html
<div id="hh">
     <p>一碗化州牛腩粉</p>
     <span>吃出男人的沉稳</span>
     <p>一碗龙江猪脚饭</p>
     <span>吃出男人的浪漫</span>
     <p>经不经典我不管</p>
     <span>我就喜欢这一款</span>
     <p>人不装逼天打雷劈</p>
     <span>装逼装的好容易当领导</span>
     <p>放心吧 在打你之前我嚼了炫迈</p>
     <span>根本停不下来</span>
</div>
```

```js
var pObjs = wyf$("hh").childNodes;
for (var i = 0; i < pObjs.length; i++) {
     if (pObjs[i].nodeType == 1 && pObjs[i].nodeName == "P") {
          pObjs[i].style.backgroundColor = "pink";
     }
}
```

### 相同标签筛选节点

```html
<input type="button" value="不是吧" id="btn">
<ul id="ll">
     <li>一碗化州牛腩粉</li>
     <li>吃出男人的沉稳</li>
     <li>一碗龙江猪脚饭</li>
     <li>吃出男人的浪漫</li>
     <li>经不经典我不管</li>
     <li>我就喜欢这一款</li>
     <li>人不装逼天打雷劈</li>
     <li>装逼装的好容易当领导</li>
</ul>
```

```js
var nodes = wyf$("ll").childNodes;
wyf$("btn").onclick = function() {
     console.log(nodes);
     count = 0;
     for (var i = 0; i < nodes.length; i++) {
          if (nodes[i].nodeType == 1 && nodes[i].nodeName == "LI") {
               nodes[i].style.backgroundColor = count % 2 == 0 ? "skyblue" : "pink";
               count++;//重点：不用i,另外设个count
          }
     }
}
```

### 	美女相册2 (切换背景)

```css
body {
     background: url("pic/咒术1.jpg") no-repeat top/cover;
}

ul {
     background-color: rgba(255, 255, 255, 0);
     list-style: none;
}

#ii {
     padding-top: 20px;
     background-color: rgba(192, 192, 192, 0.192);
     height: 200px;
     text-align: center;
}
```

```html
<div id="ii">
     <img src="./pic/咒术1.jpg" alt="">
     <img src="./pic/咒术2.jpg" alt="">
     <img src="./pic/咒术3.jpg" alt="">
</div>
```

```js
var imgObjs = wyf$("ii").children;
var count = 0;
for (var i = 0; i < imgObjs.length; i++) {
     imgObjs[i].onclick = function() {
          document.body.style.background = 'url("' + this.src + '") no-repeat top/cover';//重点为三重引号
     }
}
//正常
//'url("' + this.src + '") no-repeat top/cover'
//转义
//"url(\"" + this.src + "\") no-repeat top/cover"
//用ES6的写法，先写单撇 后加${}
//`url("${this.src}") no-repeat top/cover`
```

### 全选框，多选框

```css
td,
th {
     text-align: center;
     width: 100px;
}
```

```html
<table>
     <thead>
          <tr>
               <th>
                    <input type="checkbox" name="" id="i_th">
               </th>
               <th>&nbsp;</th>
               <th>nodeType</th>
               <th>nodeName</th>
               <th>nodeValue</th>
          </tr>
     </thead>
     <tbody id="t_td">
          <tr>
               <td>
                    <input type="checkbox" name="" id="">
               </td>
               <td>标签节点</td>
               <td>1</td>
               <td>大写的标签名</td>
               <td>属性的值</td>
          </tr>
          <tr>
               <td>
                    <input type="checkbox" name="" id="">
               </td>
               <td>属性节点</td>
               <td>2</td>
               <td>小写的属性名</td>
               <td>null</td>
          </tr>
          <tr>
               <td>
                    <input type="checkbox" name="" id="">
               </td>
               <td>文本节点</td>
               <td>3</td>
               <td>#text</td>
               <td>文本内容</td>
          </tr>
     </tbody>
</table>
```

```js
var i_th = wyf$("i_th");
var i_s = wyf$("t_td").getElementsByTagName("input");
i_th.onclick = function() {
     for (var i = 0; i < i_s.length; i++) {
          i_s[i].checked = this.checked;
     }
}//实现点击全选
for (var i = 0; i < i_s.length; i++) {
     i_s[i].onclick = function() {
          console.log(i_s[i]);
          var flag = true;//假设被全选了
          for (var j = 0; j < i_s.length; j++) {
               if (!i_s[j].checked) {
                    flag = false;//结果没全选
                    break;
               }
          }
          i_th.checked = flag;
     }
}//下面的全选完，全选框自动打勾
```

## 创建元素

### 第一种：document.write的缺陷bug，当页面加载完之后，在动作（onclick之类）里执行，他会把我们前面的内容覆盖掉

```html
<input type="button" value="document.write的加载" id="ww">fjdisvnfueovejopvnbwj经常发生滴哦
```

```js
wyf$("ww").onclick = function() {
     document.write("<p>不是吧</p>");
}
```

### 第二种：innerHTML

```html
<input type="button" value="来份牛腩粉" id="lfnnf">
<div id="nnf"></div>
```

```js
wyf$("lfnnf").onclick = function() {
     wyf$("nnf").innerHTML = "<p>牛腩粉</p>";
}
```

### 第三种：createElement（创建元素）+ appendChild（把创建的元素追加到父元素里）

```html
<input type="button" value="嗲三种创建元素的方式" id="create">
<div id="cc"></div>
```

```js
wyf$("create").onclick = function() {
     var pObj = document.createElement("p");//创建函数
     pObj.innerText = "第三种创建元素的方法";
     wyf$("cc").appendChild(pObj);//追加到父元素
}
```

### 封装一个函数（function），谁需要谁调用--加薪

```js
btn.onclick = 函数名;//直接名字调用，不用括号（），因为没有返回值
//封装的函数
function 函数名(){
     this.style.backgoundColor = "";//假设内容为把背景设为空
}
```

### 创建元素的作业，字典

```html
<input type="button" value="添加table" id="tt">
<div id="table"></div>
```

```js
var arr = [
     { name: "免费海贼王", href: "https://www.letvav.cc/dongman/haizeiwang/1-962.html" },
     { name: "复制颜色块", href: "https://flatuicolors.com/" },
     { name: "github", href: "https://github.com/" },
     { name: "在线画图", href: "https://www.processon.com/" },
     { name: "幼儿成长记", href: "http://baby.bnuz.edu.cn:8081/#/" }
];
wyf$("tt").onclick = function() {
     var tableObj = document.createElement("table");
     wyf$("table").appendChild(tableObj);
     tableObj.border = "1";
     tableObj.cellPadding = "0";
     tableObj.cellSpacing = "0";
     for (var i = 0; i < arr.length; i++) {
          var array = arr[i];
          var trObj = document.createElement("tr");
          tableObj.appendChild(trObj);
          var td1 = document.createElement("td");
          trObj.appendChild(td1);
          var td2 = document.createElement("td");
          trObj.appendChild(td2);
          td1.innerText = array.name;
          td2.innerHTML = `<a href="${array.href}">${array.name}</a>`;
     }
}
```

## 事件的方式

### 第一种

- 带on的事件onclick,onmouseover,onmouseout等等。

### 第二种（可以支持同时多个function事件反应）

- 对象.addEventListener("事件类型"，事件处理函数，false)---谷歌，火狐支持，IE等低版本不支持

  > 第一个参数：事件类型（“事件类型不带on”）
  >
  > 第二个参数：事件处理函数（匿名函数和命名函数）
  >
  > 第三个参数：false---记住事false---会涉及到后面的冒泡和捕获

```html
<input type="button" value="第二种事件方式" id="count">
```

```js
wyf$("count").addEventListener("click", function() {
     console.log("傻仔");
}, false);
wyf$("count").addEventListener("click", function() {
     console.log("好啊");
}, false);
```

### 第三种（也支持多个function事件反应）

- 对象.attachEvent("事件类型",事件处理函数)---只支持IE等地版本

  > 第一个参数：事件类型（“事件类型带on”）
  >
  > 第二个参数：事件处理函数（匿名函数和命名函数）

```html
<input type="button" value="第二种事件方式" id="count">
```

```js
wyf$("count").attachEvent("onclick", function() {
     console.log("傻仔");
});
```

## 解除事件（解绑）

### 第一种

- 事件.onclick = null;

```html
<input type="button" value="绑定事件" id="bt1">
<input type="button" value="解绑事件" id="bt2">
```

```js
wyf$("bt1").onclick = function() {
     console.log("绑定事件");
}
wyf$("bt2").onclick = function() {
     wyf$("bt2").onclick = null;//绑定事件就不起作用了
}
```

### 第二种

- 事件.removeEventListener("click",命名函数,false)

```html
<input type="button" value="绑定事件" id="bt3">
<input type="button" value="解绑事件" id="bt4">
```

```js
wyf$("bt3").addEventListener("click", f3, false);
wyf$("bt3").addEventListener("click", f4, false);
wyf$("bt4").addEventListener("click", function() {
     wyf$("bt3").removeEventListener("click", f3, false);//解除事件3，点击bt3只能实现事件4
})
```

### 第三种

- 事件.detachEvent("onclick",命名函数);

```html
<input type="button" value="绑定事件" id="bt5">
<input type="button" value="解绑事件" id="bt6">
```

```js
wyf$("bt5").attachEvent("click", f5, false);
wyf$("bt5").attachEvent("click", f6, false);
wyf$("bt6").onclick = function() {
     wyf$("bt5").removeEventListener("click", f6, false);//解除事件5，点击bt5只能实现事件6
}
```

###  冒泡事件，即点击里面小的div外面的也作出反应

- 修复这个bug的方法

  > 谷歌和火狐：e.stopPropagation();
  >
  > IE：window.event.cancelBubble = true;

```html
<div id="dv1">
     <div id="dv2">
          <div id="dv3"></div>
     </div>
</div>
```

```js
document.body.onclick = function() {
     console.log("body");//body
}
wyf$("dv1").onclick = function() {
     console.log("粉红色框");//粉红色框 body
}
wyf$("dv2").onclick = function() {
     console.log("蓝色框");//蓝色框 粉红色框 body
}
wyf$("dv3").onclick = function(e) {//事件对象event，默认写e
     console.log("黑灰色框");//黑灰色框
     //谷歌和火狐
     e.stopPropagation();
     //IE
     window.event.cancelBubble = true;
}
```

### 事件冒泡（事件委托，儿子可以委托爸爸爷爷去做，让上级做）不需要for循环tagname一个一个找了，获取所有子级 （考试）

- var target = e.target;

```html
<ul id="id">
    <li>西施</li>
    <li>王昭君</li>
    <li>貂蝉</li>
    <li>杨玉环</li>
</ul>
```

```js
wyf$("id").onclick = function(e) {//叫他爸负责接受点击事件
    var target = e.target;//target就是任意子集
    target.style.backgroundColor = "pink";
}
```

### 第二种for循环

- 数组.forEach(function(){},false)

```css
#dv1 {
    width: 300px;
    height: 300px;
    background-color: #1abc9c;
}
        
#dv2 {
    width: 200px;
    height: 200px;
    background-color: #ecf0f1;
}
        
#dv3 {
    width: 100px;
    height: 100px;
    background-color: #e74c3c;
}
```

```html
<div id="dv1">
     <div id="dv2">
          <div id="dv3"></div>
     </div>
</div>
```

```js
var dObj = [wyf$("dv1"), wyf$("dv2"), wyf$("dv3")];//获取上下几代div
dObj.forEach(function(ele) {//for循环，ele相当于i
    ele.addEventListener("click", function(e) {
        console.log(this.id);
        e.stopPropagation();//修复冒泡行为的bug
    }, false);
})
```

### 事件的三个阶段，（事件捕获，目标阶段，冒泡），后面前面的123

| 事件     | 属性                | function后面的true/false |
| -------- | ------------------- | ------------------------ |
| 事件捕获 | 1，从外往里         | true                     |
| 目标阶段 | 2，执行当前点击元素 |                          |
| 冒泡     | 3，从里到外         | false                    |

- e.evenPhase获取1，2，3

```css
#dv1 {
    width: 300px;
    height: 300px;
    background-color: #1abc9c;
}
        
#dv2 {
    width: 200px;
    height: 200px;
    background-color: #ecf0f1;
}
        
#dv3 {
    width: 100px;
    height: 100px;
    background-color: #e74c3c;
}
```

```html
<div id="dv1">
     <div id="dv2">
          <div id="dv3"></div>
     </div>
</div>
```

```js
var dObj = [wyf$("dv1"), wyf$("dv2"), wyf$("dv3")];
dObj.forEach(function(ele) {
     ele.addEventListener("click", function(e) {
          console.log(this.id + "=====" + e.eventPhase);
     }, false);//2 3 3
     ele.addEventListener("click", function(e) {
          console.log(this.id + "=====" + e.eventPhase);
     }, true);//1 1 2
})
```

### 计时器，中间的图片划过（单位：毫秒，1000毫秒=1秒）

- 设置计时器：var timeId = setInterval(fun,100);
- 关闭计时器：clearInterval(timeId);

```html
<input type="button" value="停止计时器" id="btn">
```

```js
var timedID = setInterval(fun, 100);//设置计时器
wyf$("btn").addEventListener("mouseover", function() {
    window.clearInterval(timedID);//关闭计时器
    //clearInterval(timedID);//window可以省略
}, false);
wyf$("btn").addEventListener("mouseout", function() {
    timedID = setInterval(fun, 100);//重新开启计时器
}, false);
function fun() {//另设一个func，可以减少开多个func
    console.log("计时器");
}
```

### 燥起来和停下来（抖）

```html
<input type="button" value="燥起来" id="btn1">
<input type="button" value="停起来" id="btn2">
<div id="ig">
    <img src="./pic/咚1.jpg" alt="" srcset="">
</div>
```

```js
var zao = "";//全局变量
wyf$("btn1").addEventListener("click", function() {
    zao = setInterval(dong, 100);//开启计时器
}, false);
wyf$("btn2").addEventListener("click", function() {
    window.clearInterval(zao);//关闭计时器
}, false);
function dong() {
    var x = parseInt(Math.random() * 100 + 1);//取随机数
    var y = parseInt(Math.random() * 100 + 1);
    wyf$("ig").style.left = x + "px";//要加px单位
    wyf$("ig").style.top = y + "px";
}
```

### 连续输出时间

```js
setInterval(function() {
     var dt = new Date();//获取时间
     var hour = dt.getHours();
     var min = dt.getMinutes();
     var sec = dt.getSeconds();
     console.log(hour + ":" + min + ":" + sec);
}, 1000)
```

### 自动换照片，切换照片

```html
<img src="./pic/咚1.jpg" alt="" id="change">
```

```js
function cha() {
    var mem = parseInt(Math.random() * 11 + 1);
    console.log(mem);
    wyf$("change").src = "./pic/咚" + mem + ".jpg";
}
cha();//一开始就执行一次，要不会1000毫秒才开始第一次，上面function独立就是修复这个bug
setInterval(cha, 1000);
```

### 逐渐平移

- 获取左边的left：id.offsetLeft

```html
<input type="button" value="向右移动400px" id="go">
<div id="run"></div>
```

```js
wyf$("go").addEventListener("click", function() {
     var timeId = setInterval(function() {
          var left = wyf$("run").offsetLeft;//获取绝对定位后run的left
          var step = 1;
          left += step;
          if (left <= 100) {//向右移动
               wyf$("run").style.left = left + "px";
          } else {//超过100停止
               clearInterval(timeId);
               wyf$("run").style.left = 0 + "px";
          }
     }, 10);
}, false);
```

### 逐渐平移（升级版，可以回来的）

```html
<input type="button" value="向右平移400px" id="go1">
<input type="button" value="向右平移800px" id="go2">
<input type="button" value="向右平移0px" id="go3">
<div id="dv"></div>
```

```js
function amimate(element, target) {
     clearInterval(element.timeId);//每次执行都清除定时器，以防按多次按钮加速bug
     //把定时器名字设置为element的定时器，防止每次执行func都开一个定时器
     element.timeId = setInterval(function() {
          var current = element.offsetLeft;
          //每步1px
          var step = 1;
          //判断现在位置和目标位置的前后关系
          step = current < target ? step : -step;
          current += step;
          if (Math.abs(current - target) > Math.abs(step)) {
               element.style.left = current + "px";//记住加px
          } else {
               clearInterval(element.timeId);
               element.style.left = target + "px";
          }
     }, 1);
}
```

### 箭头函数()=>{} 与function的区别

#### 1.this的指向：

- 使用**function**定义的函数，this的指向随着调用环境的变化而**变化的**，而**箭头函数**中的this指向是**固定不变的**，一直指向的是定义函数的环境。

```js
//使用function定义的函数中this指向是随着调用环境的变化而变化的
function foo(){
	console.log(this);
}
var obj = { aa: foo };
foo(); //Window
obj.aa() //obj { aa: foo }
```

```js
//明显使用箭头函数的时候，this的指向是没有发生变化的。
var foo = () => { console.log(this) };
var obj = { aa:foo };
foo(); //Window
obj.aa(); //Window
```

#### 2.构造函数：

- function是可以定义构造函数的，而箭头函数是不行的。

```js
//使用function方法定义构造函数
function Person(name, age){
	this.name = name;
	this.age = age;
}
var lenhart =  new Person(lenhart, 25);
console.log(lenhart); //{name: 'lenhart', age: 25}
```

```js
//尝试使用箭头函数
var Person = (name, age) =>{
	this.name = name;
	this.age = age;
};
var lenhart = new Person('lenhart', 25); //报错：Uncaught TypeError: Person is not a constructor
```

#### 3.变量提升

- 由于js的内存机制，function的级别最高，而用箭头函数定义函数的时候，需要var(let const定义的时候更不必说)关键词，而var所定义的变量不能得到变量提升，故箭头函数一定要定义于调用之前！

```js
foo(); //123
function foo(){
	console.log('123');
}

arrowFn(); //Uncaught TypeError: arrowFn is not a function
var arrowFn = () => {
	console.log('456');
};
```

### 轮播图（中间的图片切换）

```css
#box {
     position: relative;
     margin: 100px auto;
     width: 500px;
     height: 281px;
     box-shadow: 0px 0px 10px 5px #353b48;
     overflow: hidden;
}

#img {
     position: absolute;
}

#img ul {
     width: 20000px;
     position: absolute;
}

#img ul li {
     overflow: hidden;
     float: left;
}

#img ul li img {
     width: 500px;
}

#box ol {
     position: absolute;
     align-self: center;
     right: 6px;
     top: 90%;
}

#box ol li {
     color: #353b48;
     background-color: #ffffff;
     margin-right: 4px;
     text-align: center;
     border-radius: 10px;
     float: left;
     display: block;
     width: 20px;
     cursor: pointer;
     user-select: none;
     box-shadow: 0 0 10px 1px #ffffff;
}

.current {
     color: white !important;
     background-color: #353b48 !important;
}

.switch {
     font-size: 20px;
     color: white;
     position: absolute;
     top: 42%;
     width: 44px;
     height: 44px;
     cursor: pointer;
     background-color: rgba(0, 0, 0, 0.63);
     display: none;
     align-items: center;
     user-select: none;
}

.switch:active {
     background-color: rgba(71, 71, 71, 0.63);
}

#left {
     left: -16px;
     border-top-right-radius: 22px;
     border-bottom-right-radius: 22px;
}

#left span {
     margin-left: 50%;
}

#right {
     right: -16px;
     border-top-left-radius: 22px;
     border-bottom-left-radius: 22px;
}

#right span {
     margin-left: 22%;
}
```

```html
<div id="box" class="box">
     <div id="img">
          <ul id="ul">
               <li>
                    <a href=""><img src="./pic/咚1.jpg" alt=""></a>
               </li>
               <li>
                    <a href=""><img src="./pic/咚2.jpg" alt=""></a>
               </li>
               <li>
                    <a href=""><img src="./pic/咚3.jpg" alt=""></a>
               </li>
               <li>
                    <a href=""><img src="./pic/咚4.jpg" alt=""></a>
               </li>
          </ul>
     </div>
     <ol>
     </ol>
     <div id="left" class="switch">
          <span>&lt</span>
     </div>
     <div id="right" class="switch">
          <span>&gt</span>
     </div>
</div>
```

```js
window.onload = function() {
        //平移的封装函数
    function animate(element, target) {
        //每次执行都清除定时器，以防按多次按钮加速
        clearInterval(element.timeId);
        //把定时器名字设置为element的定时器，防止每次执行func都开一个定时器
        element.timeId = setInterval(function() {
            var current = element.offsetLeft;
            //控制平移的快慢
            var step = 15;
            //判断当前位置和目标位置的关系从而决定正反方向平移
            step = current < target ? step : -step;
            //每一次走一步
            current += step;
            //正常情况的每次平移
            if (Math.abs(current - target) > Math.abs(step)) {
                element.style.left = current + "px";
            } else {
                //最后一步的平移
                clearInterval(element.timeId);
                element.style.left = target + "px";
            }
        }, 1);
    }
    //获取最外面的框
    var box = wyf$("box");
    //获取相框
    var img = wyf$("img");
    //获取ul
    var ulObj = img.children[0];
    //获取ul下的li
    var list = ulObj.children;
    //获取相框的宽度
    var imgWidth = list[0].offsetWidth;
    //获取ol
    var olObj = box.children[1];
    //获取ol下的li
    var ol_li = olObj.children;
    // 获取right和left切换图片按键
    var swi = document.getElementsByClassName("switch");
    //把索引作为全局变量定义
    var index_this = 0;
    for (var i = 0; i < list.length; i++) {
        // 创建新元素li
        var liObj = document.createElement("li");
        //把li加进ol里
        olObj.appendChild(liObj);
        // 把第一个li设当前class
        ol_li[0].className = "current";
        // 给每个li设属性索引
        liObj.setAttribute("index", i);
        //获取索引
        var index = liObj.getAttribute("index");
        // 添加内容1234，为索引+1
        liObj.innerHTML = parseInt(index) + 1;
        // li的排他思想
        liObj.onclick = function() {
            for (var j = 0; j < ol_li.length; j++) {
                // console.log(ol_li[j].className);
                ol_li[j].removeAttribute("class");
            }
            this.className = "current";
            //获取点击的li的索引，表示第几个
            index_this = this.getAttribute("index");
            animate(img, -index_this * imgWidth);
        }
    }
    //大招，加薪，为了平移循环后面接上前面，在后面克隆上
    ulObj.appendChild(ulObj.children[0].cloneNode(true));
    //left按钮的点击事件
    wyf$("left").onclick = function() {
            // 当图片为第一个的时候点击，会向右平移并出现最后一张图片
            if (index_this == 0) {
                index_this = list.length - 1;
                img.style.left = -index_this * imgWidth + "px";
            }
            index_this--;
            //调用animate函数点击平移
            animate(img, -index_this * imgWidth);
            //下面的数字按钮用排他思想同步
            for (let i = 0; i < ol_li.length; i++) {
                ol_li[i].removeAttribute("class");
            }
            ol_li[index_this].className = "current";
        }
        //right按钮的点击事件
    wyf$("right").onclick = f_right;
    // 封装right点击事件
    function f_right() {
        if (index_this == list.length - 1) {
            index_this = 0;
            img.style.left = 0 + "px";
        }
        index_this++;
        animate(img, -index_this * imgWidth);
        if (index_this == list.length - 1) {
            ol_li[ol_li.length - 1].removeAttribute("class");
            ol_li[0].className = "current";
        } else {
            for (let i = 0; i < ol_li.length; i++) {
                ol_li[i].removeAttribute("class");
            }
            ol_li[index_this].className = "current";
        }
    }
    //给right设每秒点击一次事件，从而达成自动切换效果
    var img_move = setInterval(f_right, 3500);
    //right和left的出现和消失事件
    wyf$("box").onmouseover = function() {
        swi[0].style.display = "flex";
        swi[1].style.display = "flex";
        clearInterval(img_move);
    }
    wyf$("box").onmouseout = function() {
        swi[0].style.display = "none";
        swi[1].style.display = "none";
        img_move = setInterval(f_right, 3500);
    }
}
```

### offset系列

- offsetWidth
- offsetHeight
- offsetLeft
- offserTop

|              |              获取右边offsetLeft              |
| :----------: | :------------------------------------------: |
| 有定位的时候 |            自己的left值+margin值             |
|   标准流时   | 父级的（margin+border+padding）+自己的margin |

### document获取元素

- document.body====获取body
- document.title====获取title
- document.documentElement====获取整个

### 给鼠标添加跟随图片，小苍蝇

- e.clientX：获取鼠标X坐标
- e.clientY：获取鼠标Y坐标

```css
#insect {
    position: absolute;
    left: -100px;
    user-select: none;
    z-index: 1;
}
```

```html
<img src="./pic/蓝色苍蝇.gif" alt="" width="60" id="insect">
```

```js
document.onmousemove = function(e) {
     wyf$("insect").style.left = e.clientX + 15 + "px";
     wyf$("insect").style.top = e.clientY + 15 + "px";
}
```

